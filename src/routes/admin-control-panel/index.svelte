<script>
  import { onMount } from "svelte";
  import { parseJwt } from '../../parseJwt'

  let token = {
    adminId: ''
  }

  onMount(() => {
    let lsToken = localStorage.getItem('token') || ''
    if (lsToken !== '') {
      token = parseJwt(lsToken)
    }

    if (token.adminId === '') {
      window.location.href = '/admin-control-panel/login'
    } else if (token.adminId) {
      window.location.href = '/admin-control-panel/dashboard'
    } else {
      window.location.href = '/admin-control-panel/register'
    }
  })
</script>