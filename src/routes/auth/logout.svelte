<script>
  import { onMount } from "svelte";

  onMount(() => {
    localStorage.removeItem('token')
    
    window.location.href = '/'
  })
</script>

<svelte:head>
  <title>Logout: /community_folder/</title>
  <meta name="description" content="">
  <meta name="keywords" content="">
</svelte:head>
