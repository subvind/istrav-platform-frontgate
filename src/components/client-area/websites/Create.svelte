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

  async function createWebsite () {
    return axios
      .post(`${api}/websites`,
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

  async function createAdmin (website: any) {
    return axios
      .post(`${api}/admins`,
      {
        email: account.email,
        username,
        password,
        domainName: website.domainName
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

  async function updateWebsiteOwnerId (website: any, owner: any) {
    return axios
      .patch(`${api}/websites/${website.id}`,
      {
        ownerId: owner.id, // admin
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
    let website = await createWebsite()
    let admin = await createAdmin(website)

    // assign admin to website as owner
    let record: any = updateWebsiteOwnerId(website, admin)
    window.location.href = `/client-area/websites/${record.id}`
  }
</script>

<div class="wrapper">
  <a href={`/client-area/websites`} class="btn right black">LIST</a>
  <h4>Create Website:</h4>
  <div class="card">
    <form on:submit={(e) => submit(e)}>
      <div class="card-content">
        <div class="row">
          <div class="input-field col s6">
            <input placeholder="for-example.com" id="first_name" type="text" class="validate" bind:value={domainName}>
            <label for="first_name">Domain Name</label>
            <p>This is the address to your website; for example: (istrav.net) or (istrav.com).</p>
          </div>
          <div class="input-field col s6">
            <input placeholder="For Example" id="last_name" type="text" class="validate" bind:value={displayName}>
            <label for="last_name">Display Name</label>
            <p>This is the viewable address as it should be branded; for example: (/istrav/) or (isTrav).</p>
          </div>
        </div>
        <div class="row">
          <div class="input-field col s6">
            <input placeholder="MyTag1337" id="first_name" type="text" class="validate" bind:value={username}>
            <label for="first_name">Admin Username</label>
            <p>The Admin Control Panel username that will have access to this website.</p>
          </div>
          <div class="input-field col s6">
            <input placeholder="*******" id="last_name" type="password" class="validate" bind:value={password}>
            <label for="last_name">Admin Password</label>
            <p>The Admin Control Panel password that will be required to access this website.</p>
          </div>
        </div>
      </div>
      <div class="card-action">
        <button type="submit" class="btn green lighten-2">Submit</button>
        <a href="/client-area/websites" class="btn transparent black-text">cancel</a>
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