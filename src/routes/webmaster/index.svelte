<script>
  import { onMount } from "svelte";
  import { parseJwt } from '../../parseJwt'
  
  let session = {
    master: {
      id: ''
    }
  }

  onMount(() => {
    let token = localStorage.getItem('token')
    if (token) {
      session = parseJwt(token)
    }

    if (session.master.id === '') {
      window.location.href = '/webmaster/login'
    } else if (session.master.id) {
      window.location.href = '/webmaster/dashboard'
    } else {
      window.location.href = '/webmaster/login'
    }
  })
</script>