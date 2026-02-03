<!-- Nav.svelte -->
<nav class="nav">
	<a href="/">Home</a>
	<a href="/about">Who We Are</a>
	<a href="/qis-handbook">QIS Handbook</a>
	<a href="/events">Events</a>
	<a href="/initiatives">Initiatives</a>
	<a href="/project-catalogue">Project Catalogue</a>
	<a href="/blog">Contact</a>
</nav>

<style>
	.nav {
		background: red;
		position: fixed;
		top: 0px;
		width: 100%;
		display: flex;
		justify-content: center;
		background: #901a1e;
	}

	a {
		display: inline-block;
		padding: 0.7em 0.8em;
		color: white;
		height: 100%;
		text-decoration: none;
		position: relative;
		overflow: hidden;
		transition: color 0.3s ease;
	}

	a::before {
		content: '';
		position: absolute;
		left: 0;
		bottom: 0;
		width: 100%;
		height: 100%;
		background-color: #f9f9f9;
		transform: scaleY(0);
		transform-origin: bottom;
		transition: transform 0.3s ease;
		z-index: -1;
	}

	a:hover::before {
		transform: scaleY(1);
	}

	a:hover {
		color: #901a1e;
	}
</style>
