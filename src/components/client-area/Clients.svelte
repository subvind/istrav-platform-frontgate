<script lang="ts">
  import { onMount } from "svelte";
  
  export let account: any
  export let data: any

  onMount(() => {
    let el = document.querySelectorAll('.tabs')
    var instance = window['M'].Tabs.init(el, {});
  })
</script>
    
{#if account}
  hello world {account.email}
{/if}

{#if data}
  {JSON.stringify(data)}
{/if}