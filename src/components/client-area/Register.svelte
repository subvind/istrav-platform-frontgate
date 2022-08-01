
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
  let password = ''
  let username = ''
  let tenantReferenceId = 'my-example'

  async function login(username, password, tenantReferenceId) {
    axios.post(`${api}/clients/auth`, {
      tenantReferenceId,
      username,
      password
    })
      .then(function (response) {
        console.log(response)
        if (response.data) {
          localStorage.setItem('token', response.data)
          let token = parseJwt(response.data)
          window.location.href = `/client-area/accounts/${token.accountId}`
        } else {
          alert('unable to fetch auth token')
        }
      })
  }

	async function auth() {
    if (session.email === '') return alert('Email must be defined. Please register or login to a root account in order to get this.')
    if (username === '') return alert('Username must be defined.')
    if (password === '') return alert('Password must be defined.')
    if (tenantReferenceId === '') return alert('Tenant Reference ID must be defined.')

    axios.post(`${api}/clients`, {
      email: session.email,
      tenantReferenceId,
      username,
      password
    })
      .then(function (response) {
        console.log(response)
        if (response.data.agreement) {
          login(username, password, tenantReferenceId)
        } else {
          alert('invalid account')
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
        <p>Client Area:</p>
        <p>To begin, create a Client Area record by signing up here. Then we'll help get your website online and domain names hooked up to internet servers.</p>
      </div>
      <div class="input-field col s12">
        <input id="tenantReferenceId" type="text" class="validate" bind:value={tenantReferenceId}>
        <label for="tenantReferenceId">Tenant Reference ID</label>
        <p>This ID will be a key to your tenant record within /istrav/ and must be unique istrav.net wide.</p>
      </div>
      <div class="input-field col s12">
        <p>Root Owner:</p>
        <p>This is the account (username & password) assigned to the Tenant ID above that will have the absolute highest priveledges. Additional accounts may be assigned later.</p>
      </div>
      <div class="input-field col s12">
        <input id="username" type="text" class="validate" bind:value={username}>
        <label for="username">Username</label>
      </div>
      <div class="input-field col s12">
        <input id="password" type="password" class="validate" bind:value={password}>
        <label for="password">Password</label>
      </div>
      <br />
      <button style="margin-left: 1em;" type='submit' class="waves-effect black-text green lighten-2 btn" on:click={() => auth()}>Submit</button>
    </div>
  </div>
  <div>
    <a href="/client-area/login" class="waves-effect red lighten-2 btn" style="float: right;">LOGIN</a>
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