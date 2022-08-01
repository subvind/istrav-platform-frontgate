<script>
  import { onMount } from "svelte";

  onMount(() => {
    localStorage.removeItem('token')
    
    window.location.href = '/'
  })
</script>

<svelte:head>
  <title>Logout: /istrav/</title>
  <meta name="description" content="">
  <meta name="keywords" content="">
</svelte:head>
