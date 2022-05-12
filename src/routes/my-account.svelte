<script>
  import { onMount } from "svelte";
  import { parseJwt } from '../parseJwt'

  let session = {
    id: ''
  }

  onMount(() => {
    let token = localStorage.getItem('token')
    if (token) {
      session = parseJwt(token)
    }

    if (session.id === '') {
      window.location.href = '/client-area'
    } else if (session.id) {
      window.location.href = `/accounts/${session.id}`
    } else {
      window.location.href = '/client-area'
    }
  })
</script>