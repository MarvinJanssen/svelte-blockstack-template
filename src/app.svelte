<script>
	export let name;

	import blockstack from './blockstack';

	import SignInButton from './components/signinbutton.svelte';
	import SignOutButton from './components/signoutbutton.svelte';

	import UserProfile from './components/userprofile.svelte';
	
	var user_data = null;
	if (blockstack.isUserSignedIn())
		user_data = blockstack.loadUserData();
	else if (blockstack.isSignInPending())
		blockstack.handlePendingSignIn().then(function(data)
			{
			user_data = data;
			});
</script>
<style>
	main{
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1{
		color: #211f6d;
		font-size: 3em;
		font-weight: bold;
	}

	@media (min-width: 640px){
		main{
			max-width: none;
		}
	}
</style>
<main>
	<h1>Hello {name}</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<p>Read the <a href="https://blockstack.github.io/blockstack.js/">Blockstack.js documentation</a>.</p>
</main>
{#if !user_data}
	<SignInButton />
{:else}
	<UserProfile data={user_data} />
	<SignOutButton />
{/if}