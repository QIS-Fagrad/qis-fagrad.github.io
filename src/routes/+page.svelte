<script lang="ts">
	import full_logo from '$lib/assets/red_full_logo.webp';
	import { CircleArrowDown, ArrowUp } from '@lucide/svelte';

	import { scrollTo, scrollRef, scrollTop } from 'svelte-scrolling';

	let y: number = $state(0);
	const cutoff = 50;
</script>

<svelte:window bind:scrollY={y} />
{#if y > cutoff}
	<button
		use:scrollTo={'top'}
		class="fixed right-0 bottom-0 m-5 animate-fade-in rounded-full bg-gray-200 p-1.5 text-red shadow-black"
	>
		<ArrowUp class="size-5" stroke-width="3" />
	</button>
{:else}
	<button
		class="absolute right-0 bottom-0 left-0 z-0 mx-auto mb-4 flex justify-center lg:mb-7"
		use:scrollTo={'content'}
		title="arrow-down"
	>
		<CircleArrowDown class="size-8 text-red" />
	</button>
{/if}
<div use:scrollRef={'top'} class="flex h-dvh items-center justify-center">
	<img
		class="w-11/12 md:w-3/4 lg:w-1/2"
		src={full_logo}
		alt="Quantum Information Science Student Association"
	/>
</div>

<div class="h-screen" use:scrollRef={'content'}>
	<!-- {#each items as { image_path, title, text }} -->
	<div
		class="flex flex-col items-center gap-5 p-5 lg:h-1/2 lg:flex-row lg:p-10 lg:even:flex-row-reverse"
	>
		<div class="text-lg lg:text-2xl">
			<p>
				We are an association of students from both the University of Copenhagen (KU) and the
				Technical University of Denmark (DTU) for Quantum Information Science.
			</p>
		</div>
		<img class="" src="https://placehold.co/600x400" alt="img" />
	</div>

	<div
		class="flex flex-col items-center justify-center gap-5 bg-red p-5 text-white sm:flex-row sm:p-10 lg:h-1/2 lg:even:flex-row-reverse"
	>
		<p class="h-full w-full content-center text-lg lg:text-2xl">
			We oversee an Academic Committee, a Social Commitee and other initiatives. At these committees
			we focus on providing students with <a class="font-bold" href="/events"
				>events and opportunities</a
			> to engage in both fun and learning experiences. Have an idea for an event you would like to see
			realised? Join our committees and will help with all organizational and funding concerns. The committees
			are open to any student at DTU or at KU's Faculty of Science.
		</p>
		<img class="w-full" src="https://placehold.co/600x400" alt="img" />
	</div>
	<div
		class="flex flex-col items-center gap-5 p-5 lg:h-1/2 lg:flex-row lg:gap-10 lg:p-10 lg:even:flex-row-reverse"
	>
		<div class="text-lg lg:text-2xl">
			<p>
				The association is overseen by the QIS Fagråd, the student council from the Master of
				Science in Quantum Information Science at both KU and DTU. You can read more about us <a
					href="/about-us"
					class="font-bold">here</a
				>.
			</p>
		</div>
		<img class="" src="https://placehold.co/600x400" alt="img" />
	</div>
</div>

<!-- {/each} -->
