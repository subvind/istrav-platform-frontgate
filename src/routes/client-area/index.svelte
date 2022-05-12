<script>
  import { onMount } from "svelte";
  import { parseJwt } from '../../parseJwt'

  let session = {
    client: {
      id: ''
    }
  }

  onMount(() => {
    let token = localStorage.getItem('token')
    if (token) {
      session = parseJwt(token)
    }

    if (session.client && session.client.id === '') {
      window.location.href = '/client-area/login'
    } else if (session.client && session.client.id) {
      window.location.href = '/client-area/dashboard'
    } else {
      window.location.href = '/client-area/login'
    }
  })
</script>