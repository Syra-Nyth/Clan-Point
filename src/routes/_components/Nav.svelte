<script>
	export let segment
</script>

<style>
	a {
		color: black;
		padding-right: 10px;
	}
	
	a:hover {
		background-color: #b4b4b4;
	}

	nav {
		/* width: fit-content; */
		height: fit-content;
		text-align: center;
	}

	.dropdown {
		position: relative;
		display: inline-block;
	}
  
	.dropdown-content {
		display: none;
		position: absolute;
	}
	
	.dropdown:hover .dropdown-content {
		display: inline;
		border: 1px solid black;
	}
	
	span {
		text-align: right; 
	}
</style>

<nav class="navbar">
	<div class="dropdown">
    	<span class="title is-2 has-text-centered">⚙</span>
    	<div class="dropdown-content">
			<a class="navbar-item" class:is-active={segment === undefined} href=".">
			Display
			</a>
			<a class="navbar-item" class:is-active={segment === 'admin'} href="admin">
			Admin
			</a>
		</div>
  	</div>
</nav>