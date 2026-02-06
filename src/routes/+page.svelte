<script lang="ts">
	import Nav from '$lib/components/Nav.svelte';
</script>

<main>
	<Nav></Nav>
	<h1>Welcome to The QIS Fagråd</h1>
	<button on:click={() => alert('Thank you for visiting!')}> Click me </button>
</main>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Google+Sans:ital,opsz,wght@0,17..18,400..700;1,17..18,400..700&display=swap');

	main {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
		font-family: 'Google Sans', serif;
		text-align: center;
		background-color: #f9f9f9;
		color: #333;
	}
	h1 {
		font-weight: bold;
		font-size: 3rem;
		margin-bottom: 1rem;
		color: #901a1e;
	}
	button {
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
	button:hover {
		background-color: #721417;
	}
</style>
