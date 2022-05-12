<script>
	export let app = 'my-account'
	export let active = 'available-sessions'
</script>

{#if app === 'my-account'}
  <ul class="sidenav" style="display: visible;">
    <li><a class="subheader">Main</a></li>
    <li><a href="/my-account" class={active === 'available-sessions' ? 'active' : ''}><i class="material-icons">person</i>Usernames</a></li>
    <li><div class="divider"></div></li>
    <li><a class="subheader">Settings</a></li>
    <li><a href="/accounts/change-password" class={active === 'change-password' ? 'active' : ''}><i class="material-icons">key</i>Change Password</a></li>
    <li><a href="/accounts/subscription" class={active === 'subscription' ? 'active' : ''}><i class="material-icons">inbox</i>Subscription</a></li>
    <li><a href="/accounts/verify-email" class={active === 'verify-email' ? 'active' : ''}><i class="material-icons">mail</i>Verify Email</a></li>
    <li><div class="divider"></div></li>
  </ul>
{/if}
    
{#if app === 'client-area'}
  <ul class="sidenav" style="display: visible;">
    <li><a class="subheader">Main</a></li>
    <li><a href="/client-area/dashboard" class={active === 'dashboard' ? 'active' : ''}><i class="material-icons">dashboard</i>Dashboard</a></li>
    <li><div class="divider"></div></li>
    <li><a class="subheader">Client Area</a></li>
    <li><a href="/client-area/tenant" class={active === 'tenant' ? 'active' : ''}><i class="material-icons">business</i>Tenant</a></li>
    <li><a href="/client-area/websites" class={active === 'websites' ? 'active' : ''}><i class="material-icons">public</i>Websites</a></li>
    <li><a href="/client-area/clients" class={active === 'clients' ? 'active' : ''}><i class="material-icons">person</i>Clients</a></li>
    <li><a href="/client-area/billing" class={active === 'billing' ? 'active' : ''}><i class="material-icons">attach_money</i>Billing</a></li>
    <li><div class="divider"></div></li>
    <li><a class="subheader">Feedback</a></li>
    <li><a href="/client-area/help-desk" class={active === 'help-desk' ? 'active' : ''}><i class="material-icons">assignment_ind</i>Help Desk</a></li>
    <li><a href="/client-area/support" class={active === 'support' ? 'active' : ''}><i class="material-icons">assignment_turned_in</i>Support</a></li>
    <li><div class="divider"></div></li>
  </ul>
{/if}

<style>
	.sidenav {
    box-shadow: none;
    width: 100%;
		height: auto;
		transform: none !important;
		position: relative;
		background: transparent;
	}

	.sidenav li a,
	.sidenav li a i {
		color: #fff;
		font-size: 1.2em;;
	}

	.sidenav li a:hover {
		background-color: #111;
	}

	.sidenav li a.active {
		background-color: #64B5F6 !important;
    border-radius: 2em;
	}

	.sidenav .divider {
		background-color: #000;
	}
</style>