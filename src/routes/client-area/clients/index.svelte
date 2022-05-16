<script lang="ts">
  import Dashboard from '../../../components/layout/Dashboard.svelte'
  import Clients from '../../../components/client-area/Clients.svelte'

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

  async function getList(token: any) {
    axios
      .get(`${api}/clients`,
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
    
    getList(token)
  })
</script>

<Dashboard app="client-area" active="clients">
  <Clients account={account} data={data} />
</Dashboard>