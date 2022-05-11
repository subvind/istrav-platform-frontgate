<script lang='ts'>
  import { onMount } from 'svelte';

  import axios from 'axios'
  import { parseJwt } from '../../parseJwt'

  import { backend } from '../../stores.js';
  let api = '';
  backend.subscribe(value => {
		api = value
	})

  export let session = {
    email: ''
  }
	export let username = '';
  let password = '';
  export let referenceId = 'my-example';

  async function login() {
    if (session.email === '') return alert('Email must be defined. Please register or login to a root account in order to get this.')
    if (username === '') return alert('Username must be defined.')
    if (password === '') return alert('Password must be defined.')
    if (referenceId === '') return alert('Tenant Reference ID must be defined.')

    axios.post(`${api}/clients/auth`, {
      email: session.email,
      referenceId,
      username,
      password,
    })
      .then(function (response) {
        console.log(response)
        if (response.data.jwt.error) {
          alert(response.data.jwt.error)
        } else {
          let token = response.data.jwt
          if (token) {
            localStorage.setItem('token', token)
            let account = parseJwt(localStorage.getItem('token'))
            window.location.href = `/client-area/clients/${account.client.id}`
          } else {
            alert('unable to fetch auth token')
          }
        }
      })
  }

  onMount(() => {
    window.M.updateTextFields();
  })
</script>

<div class="contain">
  <div class="card auth" style="margin-top: 0;">
    <div class="row">
      <div class="input-field col s12">
        <p>The contents behind this folder are secured behind cryptography because of it's sensitive nature it is kept behind a lock and key. Only users that have registered below are allowed access here.</p>
      </div>
      <div class="input-field col s12">
        <input id="referenceId" type="text" class="validate" bind:value={referenceId}>
        <label for="referenceId">Tenant Reference ID</label>
      </div>
      <div class="input-field col s12">
        <input id="email" type="text" class="validate" bind:value={username}>
        <label for="email">Username</label>
      </div>
      <div class="input-field col s12">
        <input id="password" type="password" class="validate" bind:value={password}>
        <label for="password">Password</label>
      </div>
      <br />
      <button style="margin-left: 1em;" type='submit' class="waves-effect black-text green lighten-2 btn" on:click={() => login()}>Submit</button>
    </div>
  </div>
  <div>
    <a href="/client-area/register" class="waves-effect red lighten-2 btn" style="float: right;">REGISTER</a>
  </div>
</div>

<style>
  .contain {
    max-width: 400px;
    margin: 0 auto;
  }

  .auth {
    padding: 1em; 
    background: #111; 
    text-align: left;
  }
</style>