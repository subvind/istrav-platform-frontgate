<script>
  import { onMount } from "svelte";

  let community = 'communityfolder.com'
  let folder = 'example'
  let featured = {
    name: 'www',
    about: 'We DRIVE quality content by aligning your goal posts. Where users are the algorythm for deciding what goes on the Bulletin Board.'
  }
  let isCreate = true

  onMount(() => {
    window.M.updateTextFields();
  })
</script>

<div class="marketing">
  <br />
  <br />
  <br />
  <br />
  <br />
  <br />
  <div class="container">
    <div style="max-width: 500px; margin: 0 auto;">
      <h2 class="title">Social Groups</h2>
      <h3 class="description">For every community oriented thing there is a file and for ever collection of files there is a folder; we call these kinds of things social groups and everyone of them has their own unique bulletin board located on the internet.</h3>
    </div>
    <br />
    <div style="height: 4.2em;">
      <div class="folder-tabs">
        <button on:click={() => {isCreate = true; setTimeout(() => window.M.updateTextFields())}} class={`btn btn-large ${isCreate ? `red lighten-2` : `grey black-text`}`}>Create</button>
        <button on:click={() => isCreate = false} class={`btn btn-large ${isCreate ? `grey black-text` : `red lighten-2`}`}>Search</button>
      </div>
    </div>
    <div class="register">
      <br />
      <br />
      {#if isCreate === true}
        <div class="row" style="margin: 0;">
          <form class="col s12">
            <div class="row" style="margin: 0;">
              <div class="input-field col s6">
                <input placeholder="" id="first_name" type="text" class="validate" value={folder}>
                <label for="first_name">Folder</label>
              </div>
              <div class="input-field col s6">
                <input id="last_name" type="text" class="validate" value={community}>
                <label for="last_name">Community</label>
              </div>
            </div>
            <div class="row" style="margin: 0;">
              <div class="col s8">
                <button class="btn white black-text fluid">https://{folder}.{community}</button>
              </div>
              <div class="col s4">
                <button class="btn blue lighten-2 fluid">register</button>
              </div>
            </div>
          </form>
        </div>
        <br />
        <br />
      {:else}
        <div class="row" style="margin: 0;">
          <div class="col l3">
            <ul>
              <li><a class="grey-text text-lighten-3" href="#!">Startups</a></li>
              <li><a class="grey-text text-lighten-3" href="#!">Networks</a></li>
              <li><a class="grey-text text-lighten-3" href="#!">Clans</a></li>
              <li><a class="grey-text text-lighten-3" href="#!">Teams</a></li>
            </ul>
          </div>
          <div class="col l3">
            <ul>
              <li><a class="grey-text text-lighten-3" href="#!">Companies</a></li>
              <li><a class="grey-text text-lighten-3" href="#!">Websites</a></li>
              <li><a class="grey-text text-lighten-3" href="#!">Businesses</a></li>
              <li><a class="grey-text text-lighten-3" href="#!">Neighborhoods</a></li>
            </ul>
          </div>
          <div class="col l3">
            <ul>
              <li><a class="grey-text text-lighten-3" href="#!">Organizations</a></li>
              <li><a class="grey-text text-lighten-3" href="#!">Communities</a></li>
              <li><a class="grey-text text-lighten-3" href="#!">Squads</a></li>
              <li><a class="grey-text text-lighten-3" href="#!">Parties</a></li>
            </ul>
          </div>
          <div class="col l3">
            <ul>
              <li><a class="grey-text text-lighten-3" href="#!">Clubs</a></li>
              <li><a class="grey-text text-lighten-3" href="#!">Conventions</a></li>
              <li><a class="grey-text text-lighten-3" href="#!">Games</a></li>
              <li><a class="grey-text text-lighten-3" href="#!">Sports</a></li>
            </ul>
          </div>
        </div>
        <br />
      {/if}
      <br />
    </div>
    <div class="folder-footer">
      <div class="row" style="margin: 0;">
        <div class="col l6">

          <div class="center">
            <h1 class="white-text" style="margin: 0;"><i class="large material-icons">folder_special</i></h1>
            <h3 class="white-text">Today's Featured</h3>
            <br />
          </div>
        </div>
        <div class="col l6">
          <h5 class="grey-text text-lighten-4"><span style="font-weight: 900; font-size: 1.5em;">{featured.name}</span>:<br />{featured.about}</h5>
          <br />
          <a href={`https://${featured.name}.communityfolder.com`} class="btn btn-small white black-text">Checkout</a>
          <br />
          <br />
        </div>
      </div>
    </div>
    <p class="detail">(notice: Unlike other social media platforms we are not here to take over and the world. We are simply here to provide Software as a Service. That's why we gave ourselves a very specific searchable name "/community_folder/" rather than some abstract idea like "twitter" or "meta"; because we are in the business of code rather than people. That way members may fork us and run their own websites with their own rules.)</p>
  </div>
  <br />
  <br />
  <br />
  <br />
  <br />
  <br />
  <br />
  <br />
</div>

<style>
  .center {
    text-align: center;
  }
  .center h3 {
    margin: 0;
    font-size: 2.5em;
    font-weight: 900;
  }
  .fluid {
    width: 100%;
  }

  .folder-tabs {
    float: right;
    overflow: hidden;
    background: #111;
    border: 5px solid #000;
  }

  .folder-footer {
    border: 5px solid #000;
    border-top: 0;
    padding: 1em;
    background-color: #444444;    
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='4' height='4' viewBox='0 0 4 4'%3E%3Cpath fill='%23111111' fill-opacity='1' d='M1 3h1v1H1V3zm2-2h1v1H3V1z'%3E%3C/path%3E%3C/svg%3E");
  }

  .register {
    background: #333;
    border: 5px solid #111;
  }

  .marketing {
    background: #4caf50;
    color: #111;
  }

  .title {
    text-align: center;
    color: #111;
    text-align: center;
    margin: 0;
    font-size: 3em;
    font-weight: 900;
  }

  .description {
    text-align: center;
    margin: 0;
    font-size: 2em;
  }

  ul {
    text-align: center;
  }

  ul li {
    margin: 0.5em;
    font-size: 1.5em;
  }
  ul li a {
    color: #111;
  }

  .detail {
    font-size: 1.5em;
    text-align: center;
    padding: 0;
  }
</style>