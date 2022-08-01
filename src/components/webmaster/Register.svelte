
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
	let aboutPosition = ''

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
    if (aboutPosition === '') return alert('About Position must be defined.')

    axios.post(`${api}/accounts`, {
      resumeLink,
      aboutPosition
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
        <p>The Team:</p>
        <p>Are you interested in becoming a webmaster? Join an exciting team of developers and coders here at /istrav/ by submitting your resume to us and then tell us a bit about the position you are applying for.</p>
      </div>
      <div class="input-field col s12">
        <input id="resumeLink" type="text" class="validate" bind:value={resumeLink}>
        <label for="resumeLink">Resume URL</label>
      </div>
      <div class="input-field col s12">
        <textarea id="about" type="text" class="materialize-textarea" bind:value={aboutPosition}></textarea>
        <label for="about">About Position</label>
      </div>
      <br />
      <button style="margin-left: 1em;" type='submit' class="waves-effect black-text green lighten-2 btn" on:click={() => auth()}>Submit</button>
    </div>
  </div>
  <div>
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