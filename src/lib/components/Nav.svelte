<!-- Nav.svelte -->
<script>
	const navItems = [
		{ href: '/', label: 'Home' },
		{ href: '/', label: 'Who We Are' },
		{ href: '/', label: 'QIS Handbook' },
		{ href: '/', label: 'Events' },
		{ href: '/', label: 'Initiatives' },
		{ href: '/', label: 'Project Catalogue' },
		{ href: '/', label: 'Contact' }
	];
</script>

<nav class="nav">
	{#each navItems as { href, label }}
		<a {href}>{label}</a>
	{/each}
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
