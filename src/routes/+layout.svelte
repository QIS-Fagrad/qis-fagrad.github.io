<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';
	import Nav from '$lib/components/Nav.svelte';
	import type { Snippet } from 'svelte';

	let { children }: { children: Snippet } = $props();

	let open = $state(false);
</script>

<svelte:head>
	<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0" />
	<link rel="icon" href={favicon} />
</svelte:head>

<!-- <Nav /> -->

<Nav bind:open></Nav>
<main class="h-dvh {open ? 'overflow-y-hidden' : ''}">
	{@render children()}
</main>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Google+Sans:ital,opsz,wght@0,17..18,400..700;1,17..18,400..700&display=swap');
	@import url('https://fonts.cdnfonts.com/css/palatino');

	:root {
		font-family: 'Google Sans', serif;
	}
</style>
