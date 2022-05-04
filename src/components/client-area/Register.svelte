
<script>
  import { onMount } from 'svelte';

  import axios from 'axios'
  import { parseJwt } from '../../parseJwt'
  
  import { backend } from '../../stores.js';
  let api = '';
  backend.subscribe(value => {
		api = value
	})

	let email = ''
  let password = ''
  let passwordRepeat = ''
  let username = ''
  let subscribe = true
  let agreement = false
  let tenantId = ''

  async function login(username, password, tenantId) {
    axios.post(`${api}/accounts/auth`, {
      type: 'client-area',
      tenantId,
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
    if (email === '') return alert('Email must be defined.')
    if (username === '') return alert('Username must be defined.')
    if (password === '') return alert('Password must be defined.')
    if (agreement === false) return alert('Agreement must be accepted.')
    if (tenantId === '') return alert('Tenant ID must be defined.')

    axios.post(`${api}/accounts`, {
      email,
      username,
      password,
      subscribe,
      agreement
    })
      .then(function (response) {
        console.log(response)
        if (response.data.agreement) {
          login(username, password, tenantId)
        } else {
          alert('invalid account')
        }
      })
  }
</script>

<div class="contain">
  <div class="card auth" style="margin-top: 0;">
    <div class="row">
      <div class="input-field col s12">
        <input id="tenantId" type="text" class="validate" bind:value={tenantId}>
        <label for="tenantId">Tenant ID</label>
      </div>
      <div class="input-field col s12">
        <input id="email" type="email" class="validate" bind:value={email}>
        <label for="email">Email</label>
      </div>
      <div class="input-field col s12">
        <input id="username" type="text" class="validate" bind:value={username}>
        <label for="username">Username</label>
      </div>
      <div class="input-field col s12">
        <input id="password" type="password" class="validate" bind:value={password}>
        <label for="password">Password</label>
      </div>
      <div class="input-field col s12">
        <input id="passwordRepeat" type="password" class="validate" bind:value={passwordRepeat}>
        <label for="passwordRepeat">Password Confirm</label>
      </div>
      <div class="input-field col s12">
        <p>
          <label>
            <input type="checkbox" bind:checked={subscribe}  />
            <span style="color: #aaa;">Subscribe to our mailing list.</span>
          </label>
        </p>
        <p>
          <label>
            <input type="checkbox" bind:checked={agreement} />
            <span style="color: #aaa;">I have read and agree to follow the rules.</span>
          </label>
        </p>
      </div>
      <br />
      <button style="margin-left: 1em;" type='submit' class="waves-effect black-text green lighten-2 btn" on:click={() => auth()}>Submit</button>
      <a href="/rules" class="btn black grey-text" style="float: right;">RULES</a>
    </div>
  </div>
  <div>
    <a href="/credits" class="btn-flat grey-text">CREDITS</a>
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