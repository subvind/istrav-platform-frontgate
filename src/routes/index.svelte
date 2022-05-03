<script>
  import Navigation from '../components/Navigation.svelte';
  import Browser from '../components/Browser.svelte'
  import Footer from '../components/Footer.svelte'
  import Marketing from '../components/Marketing.svelte'
  import ClientAreaTitle from '../components/ClientAreaTitle.svelte';
</script>

<svelte:head>
  <title>/community_folder/: Bulletin Board Software</title>
</svelte:head>

<Navigation />

<Browser />

<Marketing />

<div class="container">
  <br />
  <br />
  <br />
  <div class="community">
    <ClientAreaTitle />
    <br />
    <br />
    <br />
    <div class="folder">
      <div class="navigation">
        <a href="/login" class="btn btn-small blue lighten-2">LOGIN</a>
        <a href="/register" class="btn btn-small blue lighten-2">REGISTER</a>
        <a href="https://www.communityfolder.com" class="btn btn-small blue lighten-2">WWW</a>
      </div>
      <div class="title">
        <a href="/">
          https://communityfolder.com
        </a>
      </div>
      <div class="box">
        <br />
        <br />
        <br />
        <br />
        <br />
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
            /community_folder/
          </a>
        </div>
        <br />
        <br />
        <br />
        <br />
        <br />
        <br />
        <br />
        <br />
        <br />
        <br />
        <br />
        <br />
        <br />
      </div>
    </div>
    <footer>© {new Date().getFullYear()} <a href="https://communityfolder.com">communityfolder.com</a>. All rights reserved.</footer>
  </div>
  <br />
  <br />
  <br />
</div>

<Footer />

<style>
  .community {
    padding: 4em 0 5em;
  }
  .folder {
    margin: 4em 0 1em 0;
    border: solid #222;
    border-width: 5px 5px 5px 5px;
  }

  .container {
    max-width: 900px;
    width: 100%;
    height: 100%;
    margin: 0 auto;
  }

  .box {
    background-color: #444444;
    /* background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='4' height='4' viewBox='0 0 4 4'%3E%3Cpath fill='%23111111' fill-opacity='1' d='M1 3h1v1H1V3zm2-2h1v1H3V1z'%3E%3C/path%3E%3C/svg%3E"); */
  }

  footer {
    text-align: center;
    color: #aaa;
  }

  a {
    color: inherit;
    text-decoration: none;
  }

  .title {
    display: flex;
    background-color: #444444;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='4' height='4' viewBox='0 0 4 4'%3E%3Cpath fill='%23111111' fill-opacity='1' d='M1 3h1v1H1V3zm2-2h1v1H3V1z'%3E%3C/path%3E%3C/svg%3E");
    font-size: 1.2em;
    width: fit-content;
    padding: 0.75em 0.5em;
    /* border-radius: 1em 1em 0 0; */
    border: solid #222;
    border-width: 5px 5px 0 5px;
    margin: -3em 0 -1em 1em;
    position: absolute;
  }

  .navigation {
    float: right;
    margin-top: -3em;
    background: #222;
    border: 5px solid #222;
    margin-right: 1em;
  }

  .pad {
    flex: 1;
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
</style>