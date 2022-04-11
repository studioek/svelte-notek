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
</script>

<div class="container">
	<h1>Svelte-NotEK</h1>
	{#if $user}
		<Profile />
	{:else}
		<Auth />
	{/if}
</div>