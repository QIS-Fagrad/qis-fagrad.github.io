<script lang="ts">
	enum AcademicYear {
		Y24_25 = '2024/2025',
		Y25_26 = '2025/2026'
	}

	type Member = { name: string; email?: string };

	const members: Record<string, Member> = Object.fromEntries(
		[
			{ name: 'João Ramos', email: 'joao.ramos@nbi.ku.dk' },
			{ name: 'Veronika Postgaard', email: 'rdz524@alumni.ku.dk' },
			{ name: 'Johan Palm', email: 'johan.palm2000@gmail.com' },
			{ name: 'Bjarne Schümann', email: 'bjarne.schuemann@gmx.de' },
			{ name: 'David Ulrich', email: 'wfd255@alumni.ku.dk' },
			{ name: 'Enrique Escobar', email: 'enriquees.fdez@gmail.com' },
			{ name: 'Jan Ljubas', email: 'jan.ljubas@gmail.com' },
			{ name: 'Tommaso Pasini' },
			{ name: 'Christina Fouseki' },
			{ name: 'Nimrod Dishi' },
			{ name: 'Christina Avram' },
			{ name: 'Hans Tønning' },
			{ name: 'Marcus Jensen' },
			{ name: 'Sebastian Nilausen' },
			{ name: 'Maddi Elorza', email: 'maddiberasategi99@outlook.es' },
			{ name: 'Asger Viggo', email: 'asgervkn@gmail.com' },
			{ name: 'Emil Henningsen', email: 'emilhenningsen3@gmail.com' },
			{ name: 'Eleni Karydi', email: 'eleni.fennec@gmail.com' }
		].map((member) => [member.name, member])
	);

	const roles: Record<AcademicYear, { name: string; role: string }[]> = {
		[AcademicYear.Y25_26]: [
			{ name: 'Bjarne Schümann', role: 'Head of Academic Committee' },
			{ name: 'Christina Avram', role: 'Vice-Head of Social Committee' },
			{ name: 'Christina Fouseki', role: 'Vice-Head of QKE' },
			{ name: 'David Ulrich', role: 'Head of Social Committee' },
			{ name: 'Enrique Escobar', role: 'Head of QKE Committee' },
			{ name: 'Hans Tønning', role: 'Vice-Treasurer' },
			{ name: 'Jan Ljubas', role: 'Senior Advisor' },
			{ name: 'João Ramos', role: 'President' },
			{ name: 'Johan Palm', role: 'Head of Public Relations' },
			{ name: 'Marcus Jensen', role: 'Vice-Head of Social Committee' },
			{ name: 'Nimrod Dishi', role: 'Vice-President' },
			{ name: 'Sebastian Nilausen', role: 'Vice-Treasurer' },
			{ name: 'Tommaso Pasini', role: 'Vice-Head of Academic Committee' },
			{ name: 'Veronika Postgaard', role: 'Treasurer' }
		],

		[AcademicYear.Y24_25]: [
			{ name: 'Asger Viggo', role: 'Head of Public Relations' },
			{ name: 'Bjarne Schümann', role: 'Vice-Head of Academic Committee' },
			{ name: 'David Ulrich', role: 'Vice-Head of Social Committee' },
			{ name: 'Eleni Karydi', role: 'President' },
			{ name: 'Emil Henningsen', role: 'Treasurer' },
			{ name: 'Enrique Escobar', role: 'Contributor' },
			{ name: 'Jan Ljubas', role: 'Head of Social Committee' },
			{ name: 'João Ramos', role: 'Vice-President' },
			{ name: 'Johan Palm', role: 'Vice-Head of Public Relations' },
			{ name: 'Maddi Elorza', role: 'Head of Academic Committee' },
			{ name: 'Veronika Postgaard', role: 'Vice-Treasurer' }
		]
	};

	let selectedYear: AcademicYear = AcademicYear.Y25_26;
</script>

<h1>Who we are</h1>

<div class="cards mt-8 mr-auto mb-16 ml-auto">
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

<div class="relative mt-16 mb-8 h-12 w-full">
	<!-- Heading centered -->
	<h1 class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 text-3xl font-semibold">
		Meet our team
	</h1>

	<!-- Dropdown aligned right -->
	<div class="absolute top-1/2 right-0 -translate-y-1/2 pr-56">
		<select class="rounded border px-3 py-1 text-red-900" bind:value={selectedYear}>
			{#each Object.values(AcademicYear) as year (year)}
				<option value={year}>{year}</option>
			{/each}
		</select>
	</div>
</div>

<div class="h-cards">
	{#each roles[selectedYear] as { name, role }}
		<section class="card">
			<img
				src="https://placehold.net/avatar.svg"
				alt="Profile"
				class="mr-auto mb-5 ml-auto rounded-full"
			/>
			<h2 class="mb-0">{name}</h2>
			<h3 class="mb-2 text-lg font-bold">{role}</h3>
			<h3 class="">{members[name].email}</h3>
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
		width: 100vw;
		gap: 2rem;
		overflow-x: auto;
		padding: 4rem 4rem;
		margin: -4rem 0;
		/*-ms-overflow-style: none;
		scrollbar-width: none;*/
	}

	.h-cards .card {
		flex: 0 0 300px;
		scroll-snap-align: start;
		box-shadow: 0 15px 35px rgba(0, 0, 0, 0.25);
		border-radius: 18px;
	}
	.h-cards > .card:first-child {
		margin-left: 10rem;
	}
	.h-cards > .card:last-child {
		margin-right: 10rem;
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
