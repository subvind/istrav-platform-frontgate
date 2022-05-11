<script lang="ts">
  import { onMount } from "svelte";
  
  export let account: any
  export let availableSessions: any

  onMount(() => {
    // let token = localStorage.getItem('token')
    // let account = parseJwt(token)
    
    console.log(account)
  })
</script>

<div class="col s12 m7">
  <!-- <a class="btn right green lighten-2" href="/webmaster/login">Welcome</a> -->
  <h4 class="header">Available Sessions:</h4>
  <h6>This is a list of available sessions for websites that you are allowed access to.</h6>
  <br />
  <div class="card horizontal black-text">
    <div class="card-stacked">
      <div class="card-content">
        {#if availableSessions.users && availableSessions.users.length}
          <table class="centered striped">
            <thead>
              <tr>
                <th>Username</th>
                <th>Location</th>
                <th>Actions</th>
              </tr>
            </thead>
            <tbody>
              {#each availableSessions.users as session}
                <tr>
                  <td>{session.username}</td>
                  <td>{session.website.domainName}</td>
                  {#if session.id === account.userId}
                    <td><a href={`//${session.website.domainName}`} class="btn red lighten-2">Current</a></td>
                  {:else}
                    <td><a href={`//${session.website.domainName}/auth/login?username=${session.username}`} class="btn grey">GOTO</a></td>
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