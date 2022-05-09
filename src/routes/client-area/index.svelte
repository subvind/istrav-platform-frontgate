<script>
  import { onMount } from "svelte";
  import { parseJwt } from '../../parseJwt'

  let token = {
    ownerId: ''
  }

  onMount(() => {
    let lsToken = localStorage.getItem('token')
    if (lsToken) {
      token = parseJwt(lsToken)
    }

    if (token.ownerId === '') {
      window.location.href = '/client-area/login'
    } else if (token.ownerId) {
      window.location.href = '/client-area/dashboard'
    } else {
      window.location.href = '/client-area/register'
    }
  })
</script>