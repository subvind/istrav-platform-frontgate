<script>
  import { onMount } from "svelte";
  import { parseJwt } from '../../parseJwt'

  let token = {
    clientId: ''
  }

  onMount(() => {
    let lsToken = localStorage.getItem('token')
    if (lsToken) {
      token = parseJwt(lsToken)
    }

    if (token.clientId === '') {
      window.location.href = '/client-area/login'
    } else if (token.clientId) {
      window.location.href = '/client-area/dashboard'
    } else {
      window.location.href = '/client-area/login'
    }
  })
</script>