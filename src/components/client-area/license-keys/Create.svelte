<script lang="ts">
  import { onMount } from "svelte";
  
  export let account: any

  import axios from 'axios'
  import { parseJwt } from "../../../parseJwt";
  import { backend } from '../../../stores.js';
  
  let username: string
  let password: string
  let domainName: string
  let displayName: string
  let token: string | null
  let api: string;
  backend.subscribe(value => {
		api = value
	})

  onMount(() => {
    token = localStorage.getItem('token')
    account = parseJwt(token)

    let el = document.querySelectorAll('.tabs')
    var instance = window['M'].updateTextFields()
  })

  async function createLicenseKey () {
    return axios
      .post(`${api}/licenseKeys`,
      {
        domainName,
        displayName,
        ownerId: null, // admin
        tenantReferenceId: account.client.tenant.referenceId
      },
      {
        headers: {
          ['Authorization']: `Bearer ${token}`
        }
      })
      .then(function (response) {
        console.log(response)
        return response.data
      })
  }

  async function submit (event: any) {
    event.preventDefault()

    // create records
    let LicenseKey = await createLicenseKey()

    window.location.href = `/client-area/license-keys/${LicenseKey.id}`
  }
</script>

<div class="wrapper">
  <a href={`/client-area/license-keys`} class="btn right black">LIST</a>
  <h4>Create License Key:</h4>
  <div class="card">
    <form on:submit={(e) => submit(e)}>
      <div class="card-content">
        <div class="row">
          <div class="input-field col s6">
            <input placeholder="for-example.com" id="first_name" type="text" class="validate" bind:value={domainName}>
            <label for="first_name">Domain Name</label>
            <p>This is the address to your website; for example: (istrav.net) or (istrav.com).</p>
          </div>
        </div>
      </div>
      <div class="card-action">
        <button type="submit" class="btn green lighten-2">Submit</button>
        <a href="/client-area/license-keys" class="btn transparent black-text">cancel</a>
      </div>
    </form>
  </div>
</div>

<style>
  h4 {
    margin: 0;
  }
  .wrapper {
    margin: 1em;
  }
  .card-content,
  .card-action {
    padding: 1em;
  }
  .input-field input {
    color: #111 !important;
    border: 0 !important;
  }
</style>