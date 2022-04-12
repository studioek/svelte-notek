<script>
	import {
		user
	} from "./sessionStore"
	import {
		supabase
	} from "./supabaseClient"
	import Auth from "./Auth.svelte";
	import Profile from "./Profile.svelte";

	user.set(supabase.auth.user())

	supabase.auth.onAuthStateChange((_, session) => {
		user.set(session.user)
	})

	document.title = "Svelte-NotEK"
</script>

<header class="navbar">
	<section class="navbar-section">
		<a href="/" class="navbar-brand mr-2">
			<h1>NotEK</h1>
		</a>
	</section>
	<section class="navbar-section">
		<div class="input-group input-inline">
			
		</div>

	</section>
</header>

<div>
	{#if $user}
		<Profile />
	{:else}
		<Auth />
	{/if}
</div>