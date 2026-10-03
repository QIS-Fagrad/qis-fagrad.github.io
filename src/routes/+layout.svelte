<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';
	import Nav from '$lib/components/Nav.svelte';
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<script src="https://kit.fontawesome.com/a99e79e741.js" crossorigin="anonymous"></script>
</svelte:head>

<!-- <Nav /> -->

<Nav></Nav>
<main>
	<slot />
</main>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Google+Sans:ital,opsz,wght@0,17..18,400..700;1,17..18,400..700&display=swap');
	@import url('https://fonts.cdnfonts.com/css/palatino');

	:global(body) {
		background-color: #f9f9f9;
	}

	:root {
		font-family: 'Google Sans', serif;
		scroll-behavior: smooth;
	}

	main {
		scroll-behavior: smooth;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		text-align: center;
		color: #333;
	}
	:global(h1) {
		font-weight: bold;
		font-size: 3rem;
		margin-bottom: 1rem;
		color: #901a1e;
	}
	:global(button) {
		padding: 0.5rem 1rem;
		font-size: 1rem;
		cursor: pointer;
		border: none;
		background-color: #901a1e;
		color: white;
		border-radius: 0.5rem;
		border-radius: 2px;
		transition: background-color 0.2s;
	}
	:global(button:hover) {
		background-color: #721417;
	}

	@media screen and (width <= 700px) {
		:root {
			font-size: 0.9em;
		}
	}
</style>
