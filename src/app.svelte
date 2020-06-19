<script>
	export let name;

	import blockstack from './blockstack';

	import SignInButton from './components/signinbutton.svelte';
	import SignOutButton from './components/signoutbutton.svelte';

	import UserProfile from './components/userprofile.svelte';
	
	import session from './usersession';

	var signin_pending = session.isSignInPending();

	var user_data = null;
	if (session.isUserSignedIn())
		user_data = session.loadUserData();
	else if (signin_pending)
		{
		session.handlePendingSignIn().then(function(data)
			{
			signin_pending = false;
			user_data = data;
			});
		// remove the authResponse GET parameter from the URL without refreshing the page:
		history && history.replaceState(null,null,window.location.href.split('?')[0]);
		}
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
{#if !signin_pending && !user_data}
	<SignInButton />
{:else}
	{#if signin_pending}
		<p>Loading...</p>
	{:else}
		<UserProfile data={user_data} />
		<SignOutButton />
	{/if}
{/if}