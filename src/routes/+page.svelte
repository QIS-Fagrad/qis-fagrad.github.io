<script lang="ts">
	let _ = 'Visitor';
</script>

<main>
	<h1>Welcome to The QIS Fagråd</h1>
	<p>Hello!</p>
	<button on:click={() => alert('Thanks for visiting Bjarne!')}> Click me </button>
</main>

<style>
	main {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
		font-family: 'Georgia', serif;
		text-align: center;
		background-color: #f9f9f9;
		color: #333;
	}
	h1 {
		font-size: 3rem;
		margin-bottom: 1rem;
		color: #901a1e;
	}
	p {
		font-size: 1.5rem;
		margin-bottom: 2rem;
		color: #666666;
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
