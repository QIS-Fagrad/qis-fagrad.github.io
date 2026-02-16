<script lang="ts">
	const members = [
		{ name: 'João Ramos', role: 'President', email: 'joao.ramos@nbi.ku.dk' },
		{ name: 'Veronika Postgaard', role: 'Treasurer' },
		{ name: 'Johan Palm', role: 'Head of Public Relations' },
		{ name: 'Bjarne Schümann', role: 'Head of Academic Committee' },
		{ name: 'David Ulrich', role: 'Head of Social Committee' },
		{ name: 'Enrique Escobar', role: 'Head of QKE Committee' }
	].sort((a, b) => a.name.localeCompare(b.name));
</script>

<h1>Who we are</h1>

<div class="cards mr-auto mb-16 ml-auto">
	<section class="card">
		<h2>Representation</h2>
		<p>
			We represent the students of the Master of Science in Quantum Information Science at the
			University of Copenhagen. We work to make sure student voices are heard.
		</p>
	</section>

	<section class="card">
		<h2>Connection</h2>
		<p>
			We act as a bridge between students and the university. We listen, raise concerns, and help
			improve both the academic and social experience of the programme.
		</p>
	</section>

	<section class="card">
		<h2>Community</h2>
		<p>
			We believe in fairness, collaboration, and growth. Our goal is to build a strong and
			supportive quantum community where students can learn and connect.
		</p>
	</section>
</div>

<div class="mb-8 flex w-full items-center justify-between pr-5 pl-5">
	<!-- Empty left slot -->
	<div class="flex w-24 items-center"></div>

	<!-- Centered heading -->
	<h1 class="text-center text-3xl font-semibold">Meet our team</h1>

	<!-- Right-aligned dropdown -->
	<div>
		<select class="rounded border px-3 py-1 text-red-900">
			<option value="2025-2026">2025–2026</option>
			<option value="2024-2025">2024–2025</option>
			<option value="2023-2024">2023–2024</option>
		</select>
	</div>
</div>

<div class="h-cards">
	{#each members as { name, role, email }}
		<section class="card">
			<img
				src="https://placehold.net/avatar.svg"
				alt="Profile"
				class="mr-auto mb-5 ml-auto rounded-full"
			/>
			<h2 class="mb-0">{name}</h2>
			<h3 class="mb-2 text-lg font-bold">{role}</h3>
			<h3 class="">{email}</h3>
		</section>
	{/each}
</div>

<style lang="postcss">
	h1 {
		font-size: 2.5rem;
		font-weight: 600;
		letter-spacing: -0.02em;
	}

	.cards {
		display: grid;
		gap: 2rem;
		max-width: 1100px;
		margin: 0 auto 16;
		background-color: transparent;
	}

	.h-cards {
		display: flex;
		gap: 2rem;
		overflow-x: auto;
		padding: 4rem 4rem;
		margin: -4rem 0;
		-ms-overflow-style: none;
		scrollbar-width: none;
	}

	.h-cards .card {
		flex: 0 0 300px;
		scroll-snap-align: start;
		box-shadow: 0 15px 35px rgba(0, 0, 0, 0.25);
		border-radius: 18px;
	}

	@media (min-width: 768px) {
		.cards {
			grid-template-columns: repeat(3, 1fr);
		}
	}

	.card {
		background: #f9f9f9;
		border-radius: 18px;
		padding: 1.5rem 2rem;
		box-shadow: 0 15px 35px rgba(0, 0, 0, 0.25);
		transition:
			transform 0.25s ease,
			box-shadow 0.25s ease;
	}

	.card:hover {
		transform: translateY(-6px);
		box-shadow: 0 25px 50px rgba(0, 0, 0, 0.35);
	}

	h2 {
		font-size: 1.4rem;
		font-weight: 600;
		color: #901a1e;
	}

	p {
		line-height: 1.6;
		color: black;
		font-size: 1rem;
	}
</style>
