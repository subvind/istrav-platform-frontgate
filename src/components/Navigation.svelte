<div class="row top">
  <div class="col m1" style="background: #111; text-align: center;">
    <nav class="green lighten-2">
      <div class="nav-wrapper">
        <a href="/" class="brand-logo center"><i class="material-icons">folder</i></a>
      </div>
    </nav>
    <!-- <MainNavigation app={app} /> -->
  </div>
  <div class="col m3" style="background: #222;">
    <nav class="black lighten-2">
      <div class="nav-wrapper">
        <a href="#" class="brand-logo center">/community_folder/</a>
      </div>
    </nav>
    <!-- <Navigation app={app} active={active} /> -->
  </div>
  <div class="col m8">
    <div class="row header">
        <nav>
          <!-- {#if app === 'my-account'} -->
            <ul class="">
              <li>
                <a href="/auth/logout">Solutions</a>
              </li>
              <li>
                <a href="/auth/logout">Product</a>
              </li>
              <li>
                <a href="/auth/logout">Pricing</a>
              </li>
              <li>
                <a href="/auth/logout">About</a>
              </li>
              <li>
                <a href="/auth/logout">Community</a>
              </li>
            </ul>
            <div class="right" style="margin: 0 1em;">
              <a class="btn grey lighten-2 black-text" href="/admin-control-panel">ACP</a>
              <a class="btn grey lighten-2 black-text" href="/client-area">Client Area</a>
            </div>
          <!-- {/if} -->
        </nav>
    </div>
  </div>
</div>
<div style="height: 4.5em;"></div>

<style>
  .brand-logo i {
    margin: 0;
  }

  .top {
    z-index: 1000;
    position: fixed;
    right: 0;
    left: 0;
    margin: 0;
    padding: 0;
  }

  .top > .col {
    margin: 0;
    padding: 0;
  }

  .top > .col .row {
    margin: 0;
  }
</style>