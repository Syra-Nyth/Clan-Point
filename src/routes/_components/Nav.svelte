<script>
  export let segment;
</script>

<style>
  /* .navbar-item {
		color: black;
	}
	
	.is-boxed {
		background-color: #f0f0f0;
		border: 1px solid black;

	} */

  nav {
    height: fit-content;
    text-align: center;
    background-color: rgba(0, 0, 0, 0);
  }

  /* .navbar-divider {
		background-color: black;
	} */

  /* .dropdown {
		position: relative;
		display: inline-block;
	} */

  /* .dropdown-content {
		display: none;
		position: absolute;
	} */

  /* .dropdown:hover .dropdown-content {
		display: inline;
		border: 1px solid black;
	} */
</style>

<nav class="navbar is-fixed-top">
  <div class="navbar-menu">
    <div class="navbar-end is-spaced">
      <div class="navbar-item has-dropdown is-hoverable">
        <span
          class="title is-2 has-text-centered navbar-link has-dropdown
          is-arrowless">
          ⚙
        </span>
        <div class="navbar-dropdown is-right is-boxed">
          <a
            class="navbar-item"
            class:is-active={segment === undefined}
            href=".">
            Display
          </a>
          <a
            class="navbar-item"
            class:is-active={segment === 'admin'}
            href="admin">
            Admin
          </a>
          <!-- <a
            class="navbar-item"
            class:is-active={segment === 'test'}
            href="test">
            Test
          </a> -->
        </div>
      </div>
    </div>
  </div>
</nav>
