<script context="module">
  export async function load(ctx) {
    let id = ctx.params.id
    return { props: { id }}
  }
</script>
  
<script lang="ts">
  import Navigation from '../../components/accounts/Navigation.svelte'

  import { onMount } from "svelte";
  
  import axios from 'axios'
  import { parseJwt } from "../../parseJwt";
  import { backend } from '../../stores.js';
  
  export let id: string
  let account: any;
  let data: any;
  let api: string;
  backend.subscribe(value => {
		api = value
	})

  async function getList(account: any, token: any) {
    axios
      .get(`${api}/accounts/${id}/availableSessions`,
      {
        headers: {
          ['Authorization']: `Bearer ${token}`
        }
      })
      .then(function (response) {
        data = response.data
        console.log(response)
      })
  }
    
  onMount(() => {
    let token = localStorage.getItem('token')
    account = parseJwt(token)
    
    getList(account, token)
  })
</script>

{#if data}
  <Navigation account={account} availableSessions={data} />
{/if}