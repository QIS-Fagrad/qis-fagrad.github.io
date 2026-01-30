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
		font-family: system-ui, sans-serif;
		text-align: center;
		background: linear-gradient(135deg, #f0f0f0, #c0c0f0);
	}
	h1 {
		font-size: 3rem;
		margin-bottom: 1rem;
	}
	p {
		font-size: 1.5rem;
		margin-bottom: 2rem;
	}
	button {
		padding: 0.5rem 1rem;
		font-size: 1rem;
		cursor: pointer;
		border: none;
		background-color: #6200ee;
		color: white;
		border-radius: 0.5rem;
	}
</style>
