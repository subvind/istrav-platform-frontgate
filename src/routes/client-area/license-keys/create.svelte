<script lang="ts">
  import Dashboard from '../../../components/layout/Dashboard.svelte'
  import Create from '../../../components/client-area/license-keys/Create.svelte'

  import { onMount } from "svelte";
  
  import axios from 'axios'
  import { parseJwt } from "../../../parseJwt";
  import { backend } from '../../../stores.js';
  
  export let id: string
  let account: any;
  let data: any;
  let api: string;
  backend.subscribe(value => {
		api = value
	})
    
  onMount(() => {
    let token = localStorage.getItem('token')
    account = parseJwt(token)
  })
</script>

<Dashboard app="client-area" active="license-keys">
  <Create account={account} />
</Dashboard>