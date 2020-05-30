<script>
	import blockstack from '../blockstack';

	function sign_in()
		{
		blockstack.redirectToSignIn();
		}
</script>
<style>
	div{
		border: 1px solid #211f6d;
		background-color: #fff;
		padding: 1em;
		border-radius: .25em;
		cursor: pointer;
		background-image: url('/blockstack-indigo.svg');
		background-position: .75em center;
		background-repeat: no-repeat;
		background-size: 2em;
		padding-left: 3.25em;
		font-weight: bold;
	}
	div:hover{
		background-color: #211f6d22;
	}
</style>
<div on:click={sign_in}>
	Sign in to Blockstack
</div>