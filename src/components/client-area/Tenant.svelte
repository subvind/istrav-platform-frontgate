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
  <h4>Tenant:</h4>
  <div class="card">
    {#if data && data.id}
      <ul class="collection with-header">
        <li class="collection-header"><h4>{data.referenceId}</h4></li>
        <li class="collection-item"><div>ID<div class="secondary-content">{data.id}</div></div></li>
        <li class="collection-item"><div>Owner ID<div class="secondary-content">{data.ownerId}</div></div></li>
        <li class="collection-item"><div>Reference ID<div class="secondary-content">{data.referenceId}</div></div></li>
      </ul>
    {:else}
      <div class="card-content">
        No record...
      </div>
    {/if}
  </div>
</div>

<style>
  h3 {
    margin: 0;
  }
  .wrapper {
    margin: 1em;
  }
  .secondary-content {
    color: #111;
  }
</style>