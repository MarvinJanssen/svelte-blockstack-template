<script>
	import blockstack from '../blockstack';

	function sign_out()
		{
		blockstack.signUserOut(document.location.href);
		}
</script>
<style>
	div{
		border: 1px solid #211f6d;
		background-color: #fff;
		padding: 1em;
		border-radius: .25em;
		cursor: pointer;
		font-weight: bold;
	}
	div:hover{
		background-color: #211f6d22;
	}
</style>
<div on:click={sign_out}>
	Sign out
</div>