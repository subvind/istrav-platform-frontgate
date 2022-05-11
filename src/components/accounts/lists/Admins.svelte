<script lang="ts">
  import { onMount } from "svelte";
  
  export let account: any
  export let availableSessions: any

  onMount(() => {
    // let token = localStorage.getItem('token')
    // let account = parseJwt(token)
    
    // console.log(availableSessions)
  })
</script>

<div class="col s12 m7">
  <a class="btn right green lighten-2" href="/admin-control-panel/login">Welcome</a>
  <h4 class="header">Available Sessions:</h4>
  <h6>This is a list of available sessions for websites that you are allowed control over.</h6>
  <br />
  <div class="card horizontal black-text">
    <div class="card-stacked">
      <div class="card-content">
        {#if availableSessions.admins && availableSessions.admins.length}
          <table class="centered striped">
            <thead>
              <tr>
                <th>Username</th>
                <th>Location</th>
                <th>Actions</th>
              </tr>
            </thead>
            <tbody>
              {#each availableSessions.admins as session}
                <tr>
                  <td>{session.username}</td>
                  <td>{session.website.domainName}</td>
                  {#if session.id === account.userId}
                    <td><a href={`/admin-control-panel`} class="btn red lighten-2">Current</a></td>
                  {:else}
                    <td><a href={`/admin-control-panel/login?domainName=${session.website.domainName}&username=${session.username}`} class="btn grey">GOTO</a></td>
                  {/if}
                </tr>
              {/each}
            </tbody>
          </table>        
        {:else}
          <p style="padding: 1em;">Empty...</p>
        {/if}
      </div>
    </div>
  </div>
</div>

<style>
  .card-content {
    padding: 0;
  }
</style>