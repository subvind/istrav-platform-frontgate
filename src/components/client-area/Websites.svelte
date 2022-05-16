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
  <a href={`/client-area/websites/create`} class="btn right black">CREATE</a>
  <h4>Websites:</h4>
  <div class="card">
    {#if data && data.length}
      <table class="centered">
        <thead>
          <tr>
            <th>Domain Name</th>
            <th>Display Name</th>
            <th style="text-align: right;">Actions</th>
          </tr>
        </thead>
        <tbody>
          {#each data as record}
            <tr>
              <td>{record.domainName}</td>
              <td>{record.displayName}</td>
              <td style="text-align: right;">
                <a href={`/client-area/websites/update/${record.id}`} class="btn btn-small grey lighten-2 black-text">Update</a>
                <a href={`/client-area/websites/delete/${record.id}`} class="btn btn-small grey lighten-2 black-text">Delete</a>
              </td>
            </tr>
          {/each}
        </tbody>
      </table>
    {:else}
      <div class="card-content">
        No records...
      </div>
    {/if}
  </div>
</div>

<style>
  h4 {
    margin: 0;
  }
  .wrapper {
    margin: 1em;
  }
</style>