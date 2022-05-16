<script lang="ts">
  import { onMount } from "svelte";
  
  export let account: any
  export let availableSessions: any

  onMount(() => {
    // let token = localStorage.getItem('token')
    // let account = parseJwt(token)
    
    // console.log(account)
  })
</script>

<div class="col s12">
  <a class="btn right black" href="/client-area/login">Welcome</a>
  <h4 class="header">Available Sessions:</h4>
  <h6>This is a list of available sessions for tenants that you have permission to.</h6>
  <br />
  <div class="card horizontal black-text">
    <div class="card-stacked">
      <div class="card-content">
        {#if availableSessions.clients && availableSessions.clients.length}
          <table class="centered striped">
            <thead>
              <tr>
                <th>Username</th>
                <th>Tenant</th>
                <th>Actions</th>
              </tr>
            </thead>
            <tbody>
              {#each availableSessions.clients as session}
                <tr>
                  <td>{session.username}</td>
                  <td>{session.tenant.referenceId}</td>
                  {#if account.client && session.id === account.client.id}
                    <td><a href={`/client-area`} class="btn red lighten-2">Current</a></td>
                  {:else}
                    <td><a href={`/client-area/login?tenantReferenceId=${session.tenant.referenceId}&username=${session.username}`} class="btn grey">GOTO</a></td>
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