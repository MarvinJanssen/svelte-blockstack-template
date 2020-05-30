<script>
	export var data;
	console.log(data);

	function show()
		{
		this.style.display = 'block';
		}
	function hide()
		{
		this.remove();
		}
</script>
<style>
	.profile{
		border: 1px solid #ccc;
		border-radius: 9999px;
		padding: 1em;
		margin-bottom: 2em;
		display: flex;
	}
	.avatar img{
		display: none;
		width: 100%;
	}
	.avatar{
		overflow: hidden;
		flex-shrink: 0;
		background-color: #eee;
		border-radius: 5em;
		width: 5em;
		height: 5em;
		margin-right: 1em;
	}
	.username{
		font-weight: bold;
		margin-bottom: 1em;
	}
	.address{
		word-break: break-all;
		font-size: .75em;
	}
</style>
<div class="profile">
	<div class="avatar">
		<img alt="Avatar" src="https://gaia.blockstack.org/hub/{data.identityAddress}//avatar-0" on:load={show} on:error={hide}>
	</div>
	<div>
		<div class="username">
			{data.username}
		</div>
		<div class="address">
			{data.identityAddress}	
		</div>
	</div>
</div>