<script lang="ts">
	import full_logo from '$lib/assets/red_full_logo.webp';
	import { CircleArrowDown, ArrowUp } from '@lucide/svelte';

	let y: number = $state(0);
	const cutoff = 50;
</script>

<svelte:window bind:scrollY={y} />
{#if y > cutoff}
	<a
		href="#top"
		class="fixed right-0 bottom-0 m-5 animate-fade-in rounded-full bg-gray-200 p-1.5 text-red shadow-black"
	>
		<ArrowUp class="size-5" stroke-width="3" />
	</a>
{:else}
	<a
		class="absolute right-0 bottom-0 left-0 z-0 mx-auto mb-4 flex justify-center lg:mb-7"
		href="#description"
		title="arrow-down"
	>
		<CircleArrowDown class="size-8 text-red" />
	</a>
{/if}
<div id="top" class="flex h-dvh items-center justify-center">
	<img
		class="w-11/12 md:w-3/4 lg:w-1/2"
		src={full_logo}
		alt="Quantum Information Science Student Association"
	/>
</div>

<div class="description" id="description"></div>
<!-- {#each items as { image_path, title, text }} -->
<div class="img-text h-1/2 even:flex-row-reverse even:bg-red even:text-white">
	<div class="w-full text-2xl">
		<p>
			We are an association of students from both the University of Copenhagen (KU) and the
			Technical University of Denmark (DTU) for Quantum Information Science.
		</p>
	</div>
	<img class="h-full" src="https://placehold.co/600x400" alt="img" />
</div>

<div class="img-text h-1/2 even:flex-row-reverse even:bg-red even:text-white">
	<div class="w-full text-2xl">
		<p>
			We oversee different such as our Academic Committee and our Social Commitee. At these
			committees we focus on providing students with <a class="font-bold text-red" href="/events"
				>events and opportunities</a
			> to engage in both fun and learning experiences. Have an idea for an event you would like to see
			realised? Join our committees and will help with all organizational and funding concerns. The committees
			are open to any student at DTU or at the KU's Faculty of Science to join.
		</p>
	</div>
	<img class="h-full" src="https://placehold.co/600x400" alt="img" />
</div>

<div class="img-text h-1/2 even:flex-row-reverse even:bg-red even:text-white">
	<div class="w-full text-2xl">
		<p>
			The association is overseen by the Fagråd (Student Council) from the Master of Science in
			Quantum Information Science at both KU and DTU. You can read more about us <a
				href="/about-us"
				class="font-bold">here</a
			>.
		</p>
	</div>
	<img class="h-full" src="https://placehold.co/600x400" alt="img" />
</div>

<!-- {/each} -->

<style>
	.img-text {
		display: flex;
		justify-content: space-between;
		align-items: center;
		height: 50vh;
	}
	.img-text > div {
		display: flex;
		flex-direction: column;
		padding: 2em 5em;
		align-content: center;
	}
	.img-text p {
		font-size: 1.1em;
	}
	@media screen and (height <= 800px) {
		.img-text {
			height: 100vh;
		}
	}
	@media screen and (width <= 1400px) {
		.img-text > img {
			height: auto;
			width: 40vw;
			padding: 2em;
		}
	}
	@media screen and (width <= 1000px) {
		.img-text:nth-child(odd),
		.img-text:nth-child(even) {
			display: flex;
			flex-direction: column;
		}
		.img-text {
			justify-content: space-between;
			align-items: center;
			height: min-content;
			padding: 2em auto;
		}
		.img-text > img {
			width: 100vw;
			padding: 0;
		}
		.img-text > div {
			padding: 1em 1em;
		}
	}
</style>
