
<script>
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

  async function login() {
    if (session.email === '') return alert('Email must be defined. Please register or login to a root account in order to get this.')
    if (username === '') return alert('Username must be defined.')
    if (password === '') return alert('Password must be defined.')

    axios.post(`${api}/masters/auth`, {
      email: session.email,
      username,
      password
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
            window.location.href = `/webmaster/masters/${account.master.id}`
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
        <p>The contents behind this folder are secured behind cryptography because of it's sensitive nature it is kept behind a lock and key. Only users that are part of the /community_folder/ developers and coders team are allowed access here.</p>
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
    <a href="/webmaster/register" class="waves-effect red lighten-2 btn" style="float: right;">REGISTER</a>
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