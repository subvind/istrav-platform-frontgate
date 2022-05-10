<script>
  import { onMount } from "svelte";

  onMount(() => {
    let el = document.querySelectorAll('.tabs')
    var instance = window['M'].Tabs.init(el, {});
  })
</script>
    
<nav class="nav-extended">
  <div class="container">

    <div class="nav-wrapper">
      <a href="/" class="brand-logo"><i class="material-icons">account_box</i>Account</a>
      <ul id="nav-mobile" class="right hide-on-med-and-down">
        <li><a href="#">travis.burandt@gmail.com</a></li>
      </ul>
    </div>
    <div class="nav-content">
      <ul class="tabs tabs-transparent">
        <li class="tab"><a class="active" href="#test1">USERS</a></li>
        <li class="tab"><a href="#test2">ADMINS</a></li>
        <li class="tab"><a href="#test3">CLIENTS</a></li>
        <li class="tab"><a href="#test4">MASTERS</a></li>
      </ul>

      <a href="/auth/logout" class="btn-floating btn-large halfway-fab waves-effect waves-light teal">
        <i class="material-icons">logout</i>
      </a>
    </div>
  </div>
</nav>

<ul class="sidenav" id="mobile-demo">
  <li><a href="sass.html">Sass</a></li>
  <li><a href="badges.html">Components</a></li>
  <li><a href="collapsible.html">JavaScript</a></li>
</ul>

<div class="container">
  <div id="test1" class="col s12">Test 1</div>
  <div id="test2" class="col s12">Test 2</div>
  <div id="test3" class="col s12">Test 3</div>
  <div id="test4" class="col s12">Test 4</div>

</div>