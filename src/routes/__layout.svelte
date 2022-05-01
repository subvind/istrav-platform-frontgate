<script>
  import { onMount } from 'svelte';
	import { backend, sidebarVisibility, sidebarActive, sidebarMode } from '../stores.js';

  let loading = true
  let api = ''
  backend.subscribe(value => {
		api = value
	})
  
  onMount(() => {
    let hostname = window.location.hostname
    if (hostname === 'localhost' || hostname === '127.0.0.1') {
      // configure server
      backend.set(`http://192.168.10.97:3000`)
    } else if (hostname === 'web-station') {
      // configure server
      backend.set(`http://developer-station:3000`)
    } else {
      // grab last 2 host words from url
      // let words = hostname.split('.')
      // let tld = words.slice((words.length - 2), words.length).join('.')
  
      // configure server
      backend.set(`https://api.communityfolder.com`)
    }
    
    // log
    console.log('api:', api)
    loading = false
  })
</script>

{#if loading}
  <!-- do nothing -->
{:else}
  <slot></slot>
{/if}

<style>
  /* label color */
  :global(.input-field label) {
    color: #E57373 !important;
  }
  /* label focus color */
  :global(.input-field input:focus + label) {
    color: #E57373 !important;
  }
  /* label underline focus color */
  :global(.input-field input) {
    color: #ccc !important;
    border-bottom: 1em solid #E57373 !important;
    box-shadow: 0 1px 0 0 #000 !important;
  }
  :global(.input-field input:focus) {
    border-bottom: 1em solid #E57373 !important;
    box-shadow: 0 1px 0 0 #000 !important;
  }
  /* valid color */
  :global(.input-field input.valid) {
    border-bottom: 1em solid #81C784 !important;
    box-shadow: 0 1px 0 0 #000 !important;
  }
  :global(.input-field input.valid + label) {
    color: #81C784 !important;
  }
  /* invalid color */
  :global(.input-field input.invalid) {
    border-bottom: 1em solid #64B5F6 !important;
    box-shadow: 0 1px 0 0 #000 !important;
  }
  :global(.input-field input.invalid + label) {
    color: #64B5F6 !important;
  }
  /* icon prefix focus color */
  :global(.input-field .prefix.active) {
    color: #000 !important;
  }
  
  :global([type="checkbox"]:checked+span:not(.lever):before) {
    border-right: 2px solid #81C784;
    border-bottom: 2px solid #81C784;
  }
</style>