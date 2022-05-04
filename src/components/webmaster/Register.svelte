
<script>
  import { onMount } from 'svelte';

  import axios from 'axios'
  import { parseJwt } from '../../parseJwt'
  
  import { backend } from '../../stores.js';
  let api = '';
  backend.subscribe(value => {
		api = value
	})

  let resumeLink = ''
	let whyJoinUs = ''
  let password = ''
  let passwordRepeat = ''
  let username = ''
  let subscribe = true
  let agreement = false

  async function login(username, password) {
    axios.post(`${api}/accounts/auth`, {
      username,
      password
    })
      .then(function (response) {
        console.log(response)
        if (response.data) {
          localStorage.setItem('token', response.data)
          let token = parseJwt(response.data)
          window.location.href = `/members/${token.userId}`
        } else {
          alert('unable to fetch auth token')
        }
      })
  }

	async function auth() {
    if (resumeLink === '') return alert('Resume URL must be defined.')
    if (whyJoinUs === '') return alert('Why Join Us must be defined.')
    if (agreement === false) return alert('Agreement must be accepted.')

    axios.post(`${api}/accounts`, {
      resumeLink,
      whyJoinUs,
      subscribe,
      agreement
    })
      .then(function (response) {
        console.log(response)
        if (response.data.agreement) {
          // login(username, password)
          alert('Thank You!')
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
        <input id="resumeLink" type="text" class="validate" bind:value={resumeLink}>
        <label for="resumeLink">Resume URL</label>
      </div>
      <div class="input-field col s12">
        <textarea id="why" type="text" class="materialize-textarea" bind:value={whyJoinUs}></textarea>
        <label for="why">Why Join Us?</label>
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
    <a href="/webmaster/login" class="waves-effect red lighten-2 btn" style="float: right;">LOGIN</a>
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