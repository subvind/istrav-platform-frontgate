<script>
  import { onMount } from "svelte";

  let community = 'istrav.net'
  let folder = 'istrav'
  let featured = {
    name: 'istrav',
    about: 'This is a Bulletin Board System for talking about application software development, building projects, deploying solutions to production, and integration with artificial inteligence.'
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
    <div style="max-width: 600px; margin: 0 auto;">
      <h2 class="title">Networks</h2>
      <h3 class="description">Where ideas are driven and oriented around multi-layered bulletin board systems.</h3>
    </div>
    <br />
    <br />
    <div style="height: 4.2em;">
      <div class="folder-tabs">
        <button on:click={() => {isCreate = true; setTimeout(() => window.M.updateTextFields())}} class={`btn btn-large ${isCreate ? `red lighten-2` : `grey black-text`}`}>Create</button>
        <button on:click={() => isCreate = false} class={`btn btn-large ${isCreate ? `grey black-text` : `red lighten-2`}`}>Search</button>
      </div>
    </div>
    <div class="folder">

      <div class="register">
        <div class="istrav">
          /v/{folder}/
        </div>
        <br />
        <br />
        {#if isCreate === true}
          <div class="row" style="margin: 0;">
            <form class="col s12">
              <div class="row" style="margin: 0;">
                <div class="input-field col s6">
                  <input placeholder="" id="first_name" type="text" class="validate" bind:value={folder}>
                  <label for="first_name">Folder</label>
                </div>
                <div class="input-field col s6">
                  <input id="last_name" type="text" class="validate" bind:value={community}>
                  <label for="last_name">Community</label>
                </div>
              </div>
              <div class="row" style="margin: 0;">
                <div class="col s8">
                  <a href={`//${folder}.${community}`} class="btn white black-text fluid" target="_blank">https://{folder}.{community}</a>
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
            <a href={`https://${featured.name}.istrav.net`} class="btn btn-small white black-text">Checkout</a>
            <br />
            <br />
          </div>
        </div>
      </div>
    </div>
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
  .istrav {
    display: flex;
    background-color: #000;
    font-size: 2em;
    width: fit-content;
    padding: 0.75em 0.5em;
    /* border-radius: 1em 1em 0 0; */
    border: solid #000;
    border-width: 5px 5px 0 5px;
    margin: -2.85em 0 -1em 1em;
    position: absolute;
    color: #fff;
  }
  .folder {
    box-shadow: 0 0 5em #333;
  }
  .container {
    max-width: 900px;
    width: 100%;
    height: 100%;
    margin: 0 auto;
  }
  
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
    margin-right: 2em;
  }

  .folder-footer {
    border: 5px solid #000;
    border-top: 0;
    padding: 1em;
    /* https://heropatterns.com/ */
    background-color: #222;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='192' height='192' viewBox='0 0 192 192'%3E%3Cpath fill='%23000000' fill-opacity='0.4' d='M192 15v2a11 11 0 0 0-11 11c0 1.94 1.16 4.75 2.53 6.11l2.36 2.36a6.93 6.93 0 0 1 1.22 7.56l-.43.84a8.08 8.08 0 0 1-6.66 4.13H145v35.02a6.1 6.1 0 0 0 3.03 4.87l.84.43c1.58.79 4 .4 5.24-.85l2.36-2.36a12.04 12.04 0 0 1 7.51-3.11 13 13 0 1 1 .02 26 12 12 0 0 1-7.53-3.11l-2.36-2.36a4.93 4.93 0 0 0-5.24-.85l-.84.43a6.1 6.1 0 0 0-3.03 4.87V143h35.02a8.08 8.08 0 0 1 6.66 4.13l.43.84a6.91 6.91 0 0 1-1.22 7.56l-2.36 2.36A10.06 10.06 0 0 0 181 164a11 11 0 0 0 11 11v2a13 13 0 0 1-13-13 12 12 0 0 1 3.11-7.53l2.36-2.36a4.93 4.93 0 0 0 .85-5.24l-.43-.84a6.1 6.1 0 0 0-4.87-3.03H145v35.02a8.08 8.08 0 0 1-4.13 6.66l-.84.43a6.91 6.91 0 0 1-7.56-1.22l-2.36-2.36A10.06 10.06 0 0 0 124 181a11 11 0 0 0-11 11h-2a13 13 0 0 1 13-13c2.47 0 5.79 1.37 7.53 3.11l2.36 2.36a4.94 4.94 0 0 0 5.24.85l.84-.43a6.1 6.1 0 0 0 3.03-4.87V145h-35.02a8.08 8.08 0 0 1-6.66-4.13l-.43-.84a6.91 6.91 0 0 1 1.22-7.56l2.36-2.36A10.06 10.06 0 0 0 107 124a11 11 0 0 0-22 0c0 1.94 1.16 4.75 2.53 6.11l2.36 2.36a6.93 6.93 0 0 1 1.22 7.56l-.43.84a8.08 8.08 0 0 1-6.66 4.13H49v35.02a6.1 6.1 0 0 0 3.03 4.87l.84.43c1.58.79 4 .4 5.24-.85l2.36-2.36a12.04 12.04 0 0 1 7.51-3.11A13 13 0 0 1 81 192h-2a11 11 0 0 0-11-11c-1.94 0-4.75 1.16-6.11 2.53l-2.36 2.36a6.93 6.93 0 0 1-7.56 1.22l-.84-.43a8.08 8.08 0 0 1-4.13-6.66V145H11.98a6.1 6.1 0 0 0-4.87 3.03l-.43.84c-.79 1.58-.4 4 .85 5.24l2.36 2.36a12.04 12.04 0 0 1 3.11 7.51A13 13 0 0 1 0 177v-2a11 11 0 0 0 11-11c0-1.94-1.16-4.75-2.53-6.11l-2.36-2.36a6.93 6.93 0 0 1-1.22-7.56l.43-.84a8.08 8.08 0 0 1 6.66-4.13H47v-35.02a6.1 6.1 0 0 0-3.03-4.87l-.84-.43c-1.59-.8-4-.4-5.24.85l-2.36 2.36A12 12 0 0 1 28 109a13 13 0 1 1 0-26c2.47 0 5.79 1.37 7.53 3.11l2.36 2.36a4.94 4.94 0 0 0 5.24.85l.84-.43A6.1 6.1 0 0 0 47 84.02V49H11.98a8.08 8.08 0 0 1-6.66-4.13l-.43-.84a6.91 6.91 0 0 1 1.22-7.56l2.36-2.36A10.06 10.06 0 0 0 11 28 11 11 0 0 0 0 17v-2a13 13 0 0 1 13 13c0 2.47-1.37 5.79-3.11 7.53l-2.36 2.36a4.94 4.94 0 0 0-.85 5.24l.43.84A6.1 6.1 0 0 0 11.98 47H47V11.98a8.08 8.08 0 0 1 4.13-6.66l.84-.43a6.91 6.91 0 0 1 7.56 1.22l2.36 2.36A10.06 10.06 0 0 0 68 11 11 11 0 0 0 79 0h2a13 13 0 0 1-13 13 12 12 0 0 1-7.53-3.11l-2.36-2.36a4.93 4.93 0 0 0-5.24-.85l-.84.43A6.1 6.1 0 0 0 49 11.98V47h35.02a8.08 8.08 0 0 1 6.66 4.13l.43.84a6.91 6.91 0 0 1-1.22 7.56l-2.36 2.36A10.06 10.06 0 0 0 85 68a11 11 0 0 0 22 0c0-1.94-1.16-4.75-2.53-6.11l-2.36-2.36a6.93 6.93 0 0 1-1.22-7.56l.43-.84a8.08 8.08 0 0 1 6.66-4.13H143V11.98a6.1 6.1 0 0 0-3.03-4.87l-.84-.43c-1.59-.8-4-.4-5.24.85l-2.36 2.36A12 12 0 0 1 124 13a13 13 0 0 1-13-13h2a11 11 0 0 0 11 11c1.94 0 4.75-1.16 6.11-2.53l2.36-2.36a6.93 6.93 0 0 1 7.56-1.22l.84.43a8.08 8.08 0 0 1 4.13 6.66V47h35.02a6.1 6.1 0 0 0 4.87-3.03l.43-.84c.8-1.59.4-4-.85-5.24l-2.36-2.36A12 12 0 0 1 179 28a13 13 0 0 1 13-13zM84.02 143a6.1 6.1 0 0 0 4.87-3.03l.43-.84c.8-1.59.4-4-.85-5.24l-2.36-2.36A12 12 0 0 1 83 124a13 13 0 1 1 26 0c0 2.47-1.37 5.79-3.11 7.53l-2.36 2.36a4.94 4.94 0 0 0-.85 5.24l.43.84a6.1 6.1 0 0 0 4.87 3.03H143v-35.02a8.08 8.08 0 0 1 4.13-6.66l.84-.43a6.91 6.91 0 0 1 7.56 1.22l2.36 2.36A10.06 10.06 0 0 0 164 107a11 11 0 0 0 0-22c-1.94 0-4.75 1.16-6.11 2.53l-2.36 2.36a6.93 6.93 0 0 1-7.56 1.22l-.84-.43a8.08 8.08 0 0 1-4.13-6.66V49h-35.02a6.1 6.1 0 0 0-4.87 3.03l-.43.84c-.79 1.58-.4 4 .85 5.24l2.36 2.36a12.04 12.04 0 0 1 3.11 7.51A13 13 0 1 1 83 68a12 12 0 0 1 3.11-7.53l2.36-2.36a4.93 4.93 0 0 0 .85-5.24l-.43-.84A6.1 6.1 0 0 0 84.02 49H49v35.02a8.08 8.08 0 0 1-4.13 6.66l-.84.43a6.91 6.91 0 0 1-7.56-1.22l-2.36-2.36A10.06 10.06 0 0 0 28 85a11 11 0 0 0 0 22c1.94 0 4.75-1.16 6.11-2.53l2.36-2.36a6.93 6.93 0 0 1 7.56-1.22l.84.43a8.08 8.08 0 0 1 4.13 6.66V143h35.02z'%3E%3C/path%3E%3C/svg%3E");
  }

  .register {
    background: #333;
    border: 5px solid #000;
  }

  .marketing {
    background-color: #ddd;
    color: #111;
    min-height: 100vh;
    box-shadow: inset 0 0.2em 0.2em #888;
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