<script>
  import Login from "../components/auth/Login.svelte";
</script>

<svelte:head>
  <title>Login - Client Area - /community_folder/</title>
  <meta name="description" content="">
  <meta name="keywords" content="">
</svelte:head>

<div class="container">
  <div class="community">
    <div class="folder">
      <div class="navigation">
        <a href="/login" class="btn btn-small teal lighten-2">LOGIN</a>
        <a href="/register" class="btn btn-small teal lighten-2">REGISTER</a>
        <a href="https://www.communityfolder.com" class="btn btn-small teal lighten-2">WWW</a>
      </div>
      <div class="title">
        <a href="/">
          /community_folder/
        </a>
      </div>
      <div class="box">
        <br />
        <br />
        <br />
        <br />
        <br />
        <div class="stamp">
          <a class="logo" href="https://communityfolder.com">
            /community_folder/login/
          </a>
        </div>
        <div class="single"></div>
        <Login />
        <br />
        <br />
        <br />
        <br />
        <br />
      </div>
    </div>
    <footer>© {new Date().getFullYear()} <a href="https://communityfolder.com">communityfolder.com</a>. All rights reserved.</footer>
  </div>
</div>

<style>
  .community {
    padding: 2em 0;
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
    background: #444;
  }

  footer {
    text-align: center;
  }

  a {
    color: inherit;
    text-decoration: none;
  }

  .title {
    display: flex;
    background-color: #444;
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

  .start-finish {
    background-color: #333333;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='80' height='80' viewBox='0 0 80 80'%3E%3Cg fill='%23444' fill-opacity='0.4'%3E%3Cpath fill-rule='evenodd' d='M0 0h40v40H0V0zm40 40h40v40H40V40zm0-40h2l-2 2V0zm0 4l4-4h2l-6 6V4zm0 4l8-8h2L40 10V8zm0 4L52 0h2L40 14v-2zm0 4L56 0h2L40 18v-2zm0 4L60 0h2L40 22v-2zm0 4L64 0h2L40 26v-2zm0 4L68 0h2L40 30v-2zm0 4L72 0h2L40 34v-2zm0 4L76 0h2L40 38v-2zm0 4L80 0v2L42 40h-2zm4 0L80 4v2L46 40h-2zm4 0L80 8v2L50 40h-2zm4 0l28-28v2L54 40h-2zm4 0l24-24v2L58 40h-2zm4 0l20-20v2L62 40h-2zm4 0l16-16v2L66 40h-2zm4 0l12-12v2L70 40h-2zm4 0l8-8v2l-6 6h-2zm4 0l4-4v2l-2 2h-2z'/%3E%3C/g%3E%3C/svg%3E");
  }

  .single {
    margin-bottom: -3em;
    height: 10em;
    width: 0;
    border-right: 1em solid #222;
    margin: 0 auto;
  }
</style>