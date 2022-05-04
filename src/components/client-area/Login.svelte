
<script>
  import { onMount } from 'svelte';

  import axios from 'axios'
  import { parseJwt } from '../../parseJwt'

  import { backend } from '../../stores.js';
  let api = '';
  backend.subscribe(value => {
		api = value
	})

	let username = '';
  let password = '';
  let tenantId = 'my-example';

  async function login() {
    if (username === '') return alert('Username must be defined.')
    if (password === '') return alert('Password must be defined.')
    if (tenantId === '') return alert('Tenant ID must be defined.')

    axios.post(`${api}/accounts/auth`, {
      type: 'client-area',
      tenantId,
      username,
      password,
    })
      .then(function (response) {
        console.log(response)
        if (response.data) {
          localStorage.setItem('token', response.data)
          let token = parseJwt(response.data)
          window.location.href = `/client-area/accounts/${token.userId}`
        } else {
          alert('unable to fetch auth token')
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
        <input id="tenantId" type="text" class="validate" bind:value={tenantId}>
        <label for="tenantId">Tenant ID</label>
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