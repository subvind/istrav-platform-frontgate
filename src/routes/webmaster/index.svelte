<script>
  import { onMount } from "svelte";
  import { parseJwt } from '../../parseJwt'

  let token = {
    masterId: ''
  }

  onMount(() => {
    let lsToken = localStorage.getItem('token')
    if (lsToken) {
      token = parseJwt(lsToken)
    }

    if (token.masterId === '') {
      window.location.href = '/webmaster/login'
    } else if (token.masterId) {
      window.location.href = '/webmaster/dashboard'
    } else {
      window.location.href = '/webmaster/login'
    }
  })
</script>