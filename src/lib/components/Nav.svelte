<!-- Nav.svelte -->
<script lang="ts">
	import logo from '$lib/assets/red_logo.webp';

	import { page } from '$app/state'; // replace $app/stores with $app/state
	interface NavItem {
		href: string;
		label: string;
	}
	let open = false;
	const navItems: NavItem[] = [
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
	<div>
		<button
			class:open
			on:click={() => {
				open = !open;
			}}
			aria-label="burguer-menu"
		>
			<i class="fa-solid fa-bars"></i>
		</button>
		<button
			class={!open ? 'open' : ''}
			on:click={() => {
				open = !open;
			}}
			aria-label="burguer-menu"
		>
			<i class="fa-solid fa-x"></i>
		</button>
		<div class="menu" class:open>
			{#each navItems as { href, label }}
				<a
					on:click={() => (open = !open)}
					{href}
					class="item"
					class:selected={page.url.pathname === href}
					>{label}
				</a>
			{/each}
		</div>
	</div>
	<a href="/" aria-label="home-logo">
		<img class="h-15" class:opacity-0={page.url.pathname === '/'} src={logo} alt="logo" /></a
	>
</nav>

<style>
	.nav {
		font-size: 1.2em;
		padding: 0.5em;
		position: absolute;
		top: 0;
		height: min-content;
		width: 100vw;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	.nav button {
		display: None;
	}
	.menu {
		display: flex;
		justify-content: space-between;

		align-items: center;
		gap: 0.5em;
	}

	a.item {
		display: inline-block;
		padding: 0 1.5em;
		color: #901a1e;
		background-color: #f9f9f9;
		height: 100%;
		align-items: stretch;

		border-radius: 2em;
		border: 0.1em solid #901a1e;

		transition: color 0.6s ease;
		transition: background-color 0.6s ease;
	}
	a.item.selected {
		font-weight: bold;
		border-width: 0.15em;
	}

	a.item:hover {
		color: #f9f9f9;
		background-color: #901a1e;
	}

	.nav button {
		background-color: transparent;
		color: #901a1e;
		padding: auto 0.3em;
		height: 100%;
	}
	.nav button > * {
		background-color: transparent;
		height: 100%;
	}

	@media screen and (width <= 1400px) {
		.nav {
			height: 7vh;
		}
		.nav button {
			display: inline-block;
			animation: fadeIn 0.2s ease-out;
		}
		.nav button.open {
			display: none;
			animation: fadeOut 0.2s ease-out;
		}
		.nav .menu {
			display: none;
			gap: 0;
		}

		@keyframes fadeIn {
			from {
				opacity: 0;
			}
			to {
				opacity: 1;
			}
		}
		@keyframes fadeOut {
			from {
				opacity: 0;
			}
			to {
				opacity: 1;
				display: none;
			}
		}
		@keyframes slideInLeft {
			from {
				transform: translateX(-100%);
				opacity: 0;
			}
			to {
				transform: translateY(0);
				opacity: 1;
			}
		}
		@keyframes slideOutLeft {
			from {
				transform: translateX(0);
				opacity: 1;
			}
			to {
				transform: translateX(-100%);
				opacity: 0;
			}
		}
		.nav .menu.open {
			position: absolute;
			left: 0;
			top: 7vh;

			display: grid;
			grid-template-columns: auto;
			border: 0.1em solid #901a1e;

			animation: slideInLeft 0.2s ease-out;
		}
		.nav .menu .item {
			border: none;
			border-radius: 0;
			padding: 0.5em 1.5em;
		}
	}
</style>
