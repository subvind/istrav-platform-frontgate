<script lang="ts">
  import { onMount } from "svelte";
  import Users from "./lists/Users.svelte";
  import Admins from "./lists/Admins.svelte";
  import Clients from "./lists/Clients.svelte";
  import Masters from "./lists/Masters.svelte";

  export let account: any
  export let availableSessions: any

  onMount(() => {
    let el = document.querySelectorAll('.tabs')
    var instance = window['M'].Tabs.init(el, {});
  })
</script>
    
<nav class="nav-extended">
  <div class="nav-content" style="text-align: center;">
    <ul class="tabs tabs-transparent">
      <li class="tab"><a class="active" href="#test1">USERS</a></li>
      <li class="tab"><a href="#test2">ADMINS</a></li>
      <li class="tab"><a href="#test3">CLIENTS</a></li>
      <li class="tab"><a href="#test4">MASTERS</a></li>
      <!-- <li class="tab right"><a href="#test5">travis.burandt@gmail.com</a></li> -->
    </ul>
  </div>
</nav>
<br />
<div id="test1">
  <Users account={account} availableSessions={availableSessions} />
</div>
<div id="test2">
  <Admins account={account} availableSessions={availableSessions} />
</div>
<div id="test3">
  <Clients account={account} availableSessions={availableSessions} />
</div>
<div id="test4">
  <Masters account={account} availableSessions={availableSessions} />
</div>