<!-- Nav.svelte -->
<script>
	const navItems = [
		{ href: '/', label: 'Home' },
		{ href: '/who-we-are', label: 'Who We Are' },
		{ href: '/qis-handbook', label: 'QIS Handbook' },
		{ href: '/events', label: 'Events' },
		{ href: '/initiatives', label: 'Initiatives' },
		{ href: '/project-catalogue', label: 'Project Catalogue' },
		{ href: '/contact', label: 'Contact' }
	];
</script>

<nav class="nav">
	{#each navItems as { href, label }}
		<a {href}>{label}</a>
	{/each}
</nav>

<style>
	.nav {
		background: #901a1e;
		position: relative;
		top: 0;
		width: 100%;
		display: flex;
		justify-content: center;
		margin-bottom: 4em;
	}

	a {
		display: inline-block;
		padding: 0.7em 0.8em;
		color: white;
		text-decoration: none;
		transition: color 0.6s ease;
		transition: background-color 0.6s ease;
	}

	a:hover {
		color: #901a1e;
		background-color: #f9f9f9;
	}
</style>
