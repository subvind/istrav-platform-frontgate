<script lang="ts">
  import { session } from "$app/stores";
import { onMount } from "svelte";
  
  export let account: any
  export let availableSessions: any

  onMount(() => {
    // let token = localStorage.getItem('token')
    // let account = parseJwt(token)
    
    // console.log(availableSessions)
  })
</script>

<div class="col s12">
  <a class="btn right black" href="/webmaster/login">Welcome</a>
  <h4 class="header">Available Sessions:</h4>
  <h6>This is a list of available sessions for root privileges.</h6>
  <br />
  <div class="card horizontal black-text">
    <div class="card-stacked">
      <div class="card-content">
        {#if availableSessions.masters && availableSessions.masters.length}
          <table class="centered striped">
            <thead>
              <tr>
                <th>Username</th>
                <th>Actions</th>
              </tr>
            </thead>
            <tbody>
              {#each availableSessions.masters as session}
                <tr>
                  <td>{session.username}</td>
                  {#if account.master && session.id === account.master.id}
                    <td><a href={`/webmaster`} class="btn red lighten-2">Current</a></td>
                  {:else}
                    <td><a href={`/webmaster/login?username=${session.username}`} class="btn grey">GOTO</a></td>
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
  .header {
    margin-top: 0;
  }
  
  .card-content {
    padding: 0;
  }
</style>