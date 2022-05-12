<script lang="ts">
  import { onMount } from "svelte";
  import { parseJwt } from '../../parseJwt'

  let session = {
    admin: {
      id: ''
    }
  }

  onMount(() => {
    let token = localStorage.getItem('token')
    if (token) {
      session = parseJwt(token)
    }

    if (session.admin && session.admin.id === '') {
      window.location.href = '/admin-control-panel/login'
    } else if (session.admin && session.admin.id) {
      window.location.href = '/admin-control-panel/dashboard'
    } else {
      window.location.href = '/admin-control-panel/login'
    }
  })
</script>