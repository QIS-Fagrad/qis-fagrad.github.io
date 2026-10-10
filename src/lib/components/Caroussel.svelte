<!-- Caroussel.svelte -->
<script lang="ts">
	import { ChevronLeft, ChevronRight } from '@lucide/svelte';
	import { flip } from 'svelte/animate';
	import { fade } from 'svelte/transition';

	let { imgs, class: style = '' }: { imgs: string[]; class?: string } = $props();

	let curr = $state(0);

	const dot_range = $derived([...Array(5).keys()].map((v) => v + curr - 2));
</script>

<div
	class="relative z-10 aspect-16/10 w-full min-w-fit overflow-hidden rounded-xl lg:w-5xl lg:max-w-1/2 {style}"
>
	<ul class="flex h-full w-full flex-row"></ul>
	{#each imgs as img, i}
		<img
			class="absolute top-0 right-0 left-0 z-10 h-full w-full object-cover"
			style="transform: translateX(calc(100% * {i - curr})); transition-duration: {350}ms;"
			src={img}
			alt="img"
		/>
	{/each}
	{#if curr > 0}
		<button
			transition:fade
			class="pointer absolute top-0 bottom-0 left-0 z-10 mx-1 my-auto h-min rounded-full bg-red text-white opacity-65 lg:mx-3"
			onclick={() => (curr -= 1)}
		>
			<ChevronLeft class="size-5 lg:size-6" stroke-width="3" /></button
		>
	{/if}
	{#if curr < imgs.length - 1}
		<button
			transition:fade
			class="pointer absolute top-0 right-0 bottom-0 z-10 mx-1 my-auto h-min rounded-full bg-red text-white opacity-65 lg:mx-3"
			onclick={() => (curr += 1)}
		>
			<ChevronRight class="size-5 lg:size-6" stroke-width="3" /></button
		>
	{/if}

	{#if imgs.length > 1}
		<ul
			class="absolute right-0 bottom-0 left-0 z-10 m-3 mx-auto flex h-min items-center justify-center gap-2 rounded-full"
		>
			{#each dot_range as i (i)}
				{@const small = Math.abs(i - curr) == 2}
				<li
					animate:flip
					class="rounded-full bg-red {small
						? 'h-1 w-1 lg:h-2 lg:w-2'
						: 'h-2 w-2 lg:h-3 lg:w-3'} {curr == i ? 'opacity-65' : 'opacity-35'} {!(
						i >= 0 && i < imgs.length
					) && 'hidden'}"
				></li>
			{/each}
		</ul>
	{/if}
</div>
