<script lang="ts">
  import { onMount } from "svelte";
  
  export let account: any
  export let data: any

  onMount(() => {
    let el = document.querySelectorAll('.tabs')
    var instance = window['M'].Tabs.init(el, {});
  })
</script>

<!-- {#if data}
  {JSON.stringify(data)}
{/if} -->

<div class="wrapper">
  <a href={`/client-area/clients/create`} class="btn right black lighten-2">CREATE</a>
  <h4>Clients</h4>
  <div class="card">
    <table class="centered">
      <thead>
        <tr>
          <th>Username</th>
          <th style="text-align: right;">Actions</th>
        </tr>
      </thead>
      <tbody>
        {#if data}
          {#each data as record}
            <tr>
              <td>{record.username}</td>
              <td style="text-align: right;">
                <a href={`/client-area/clients/update/${record.id}`} class="btn btn-small grey lighten-2 black-text">Update</a>
                <a href={`/client-area/clients/delete/${record.id}`} class="btn btn-small grey lighten-2 black-text">Delete</a>
              </td>
            </tr>
          {/each}
        {/if}
      </tbody>
    </table>
  </div>
</div>

<style>
  h3 {
    margin: 0;
  }
  .wrapper {
    margin: 1em;
  }
</style>