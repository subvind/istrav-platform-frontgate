<script>
  import { onMount } from "svelte";
  
  import { parseJwt } from "../../parseJwt";
  
  import Login from "../../components/auth/Login.svelte";
  import Navigation from '../../components/Navigation.svelte';
  import NavigationAuth from "../../components/NavigationAuth.svelte";
  import Footer from "../../components/Footer.svelte";

  let token = {
    id: ''
  }

  onMount(() => {
    let lsToken = localStorage.getItem('token')
    if (lsToken) {
      token = parseJwt(lsToken)
      if (token.id) {
        window.location.href = `/accounts/${token.id}`
      }
    }
  })
</script>

<svelte:head>
  <title>Login: /istrav/</title>
  <meta name="description" content="">
  <meta name="keywords" content="">
</svelte:head>

<Navigation />
<NavigationAuth />

<div class="container">
  <br />
  <br />
  <br />
  <br />
  <br />
  <br />
  <br />
  <br />
  <div class="stamp">
    <a class="logo" href="/">
      /istrav/
    </a>
  </div>
  <div class="single"></div>
  <Login />
  <br />
  <br />
  <br />
  <br />
  <br />
  <br />
  <br />
  <br />
</div>

<Footer />

<style>
  .container {
    min-height: 100vh;
  }

  .container {
    max-width: 900px;
    width: 100%;
    height: 100%;
    margin: 0 auto;
  }

  a {
    color: inherit;
    text-decoration: none;
  }
  
  .stamp {
    text-align: center;
  }

  .logo {
    background: #222;
    padding: 1em;
    font-size: 2em;
    margin: 3em auto;
    width: 100px;
  }

  .single {
    margin-bottom: -3em;
    height: 10em;
    width: 0;
    border-right: 1em solid #222;
    margin: 0 auto;
  }
</style>