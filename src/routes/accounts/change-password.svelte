<script lang="ts">
  import Dashboard from '../../components/layout/Dashboard.svelte'

  import { onMount } from "svelte";
  
  import { parseJwt } from "../../parseJwt";
  import { backend } from '../../stores.js';
  
  let account: any;
  let api: string;
  backend.subscribe(value => {
		api = value
	})
    
  onMount(() => {
    let token = localStorage.getItem('token')
    account = parseJwt(token)
  })
</script>

<Dashboard app="my-account" active="change-password">
  change password
</Dashboard>
