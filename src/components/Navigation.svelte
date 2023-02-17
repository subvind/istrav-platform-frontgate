<script>
  let homepage = '//istrav.com'
</script>

<div class="row top">
  <div class="col m1" style="background: #111; text-align: center;">
    <nav class="white">
      <div class="nav-wrapper" style="text-align: center;">
        <ul>
          <li style="float: none;">
            <a href="https://istrav.com" alt="isTrav" style="height: 64px;">
              <img src="/anchor.png" alt="about" style="height: 50px; margin: 0.5em 0;">
            </a>
          </li>
        </ul>
      </div>
    </nav>
    <!-- <MainNavigation app={app} /> -->
  </div>
  <div class="col m3" style="background: #222;">
    <nav class="black lighten-2">
      <div class="nav-wrapper">
        <a href="/" class="brand-logo center">/istrav/</a>
      </div>
    </nav>
    <!-- <Navigation app={app} active={active} /> -->
  </div>
  <div class="col m8">
    <div class="row header">
        <nav class="blue lighten-2">
          <!-- {#if app === 'my-account'} -->
            <ul>
              <li>
                <a href="//istrav.com/production" class="black-text">Production</a>
              </li>
              <li>
                <a href="//istrav.com/innovation" class="black-text">Innovation</a>
              </li>
              <li>
                <a href="//istrav.com/platforms" class="black-text">Platforms</a>
              </li>
              <li>
                <a href="//istrav.com/apps" class="black-text">Apps</a>
              </li>
              <li>
                <a href="//istrav.com/projects" class="black-text">Projects</a>
              </li>
            </ul>
            <div class="right" style="margin: 0 1em;">
              <a class="btn black white-text" href={`/create-social-group`}><i class="material-icons left" style="line-height: 37px;">add</i>Social Group</a>
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