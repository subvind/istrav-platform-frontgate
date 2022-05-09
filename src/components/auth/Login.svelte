
<script>
  import { onMount } from 'svelte';

  import axios from 'axios'
  import { parseJwt } from '../../parseJwt'

  import { backend } from '../../stores.js';
  let api = '';
  backend.subscribe(value => {
		api = value
	})

	let email = '';
  let password = '';

  async function login() {
    if (email === '') return alert('Emai must be defined.')
    if (password === '') return alert('Password must be defined.')

    axios.post(`${api}/accounts/auth`, {
      email,
      password
    })
      .then(function (response) {
        console.log(response)
        let token = response.data.jwt
        if (token) {
          localStorage.setItem('token', JSON.stringify(token))
          let lsToken = parseJwt(localStorage.getItem('token'))
          window.location.href = `/accounts/${lsToken.id}`
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
    <h3 class="title">Login</h3>
    <div class="row">
      <div class="input-field col s12">
        <input id="email" type="text" class="validate" bind:value={email}>
        <label for="email">Email</label>
      </div>
      <div class="input-field col s12">
        <input id="password" type="password" class="validate" bind:value={password}>
        <label for="password">Password</label>
      </div>
      <br />
      <button style="margin-left: 1em;" type='submit' class="waves-effect black-text green lighten-2 btn" on:click={() => login()}>Submit</button>
      <a href="/rules" class="btn black grey-text" style="float: right;">RULES</a>
    </div>
  </div>
  <div>
    <a href="/auth/reset" class="btn-flat grey-text">I FORGOT MY PASSWORD</a>
    <a href="/auth/register" class="waves-effect red lighten-2 btn" style="float: right;">REGISTER</a>
  </div>
</div>

<style>
  .title {
    text-align: center;
    margin: 0 0 0.5em;
  }

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