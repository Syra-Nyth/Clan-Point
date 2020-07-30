<script>
	export let segment
</script>

<style>
	a {
		color: black;
		background-color: lightgrey;
		padding: 3px 10px;
		border-bottom: 1px solid white;
	}
	
	.is-active {
		border-bottom: 1px solid black;
	}

	nav {
		width: fit-content;
		margin: 0 auto;
	}
	
</style>

<nav class="navbar">
  <div class="navbar-brand">
    <a class="navbar-item" class:is-active={segment === undefined} href=".">
		Display
	</a>
	<a class="navbar-item" class:is-active={segment === 'admin'} href="admin">
		Admin
	</a>
  </div>
</nav>