<!-- Caroussel.svelte -->
<script lang="ts">
	import { ChevronLeft, ChevronRight } from '@lucide/svelte';

	let { imgs }: { imgs: string[] } = $props();

	let curr = $state(0);
</script>

<div
	class="relative z-10 aspect-16/10 w-full min-w-fit overflow-hidden rounded-xl lg:w-5xl lg:max-w-1/2"
>
	{#each imgs as img, i}
		<img
			class="absolute top-0 right-0 left-0 z-10 h-full w-full object-cover"
			style="
                        transform: translateX(calc(100% * {i - curr}));
                        transition-duration: {350}ms;
                    "
			src={img}
			alt="img"
		/>
	{/each}
	{#if curr > 0}
		<button
			class="pointer absolute top-0 bottom-0 left-0 z-10 mx-1 my-auto h-min rounded-full bg-red text-white opacity-65 sm:mx-3"
			onclick={() => (curr -= 1)}
		>
			<ChevronLeft class="size-5 sm:size-8" stroke-width="3" /></button
		>
	{/if}
	{#if curr < imgs.length - 1}
		<button
			class="pointer absolute top-0 right-0 bottom-0 z-10 mx-1 my-auto h-min rounded-full bg-red text-white opacity-65 sm:mx-3"
			onclick={() => (curr += 1)}
		>
			<ChevronRight class="size-5 sm:size-8" stroke-width="3" /></button
		>
	{/if}

	{#if imgs.length > 1}
		<div
			class="absolute right-0 bottom-0 left-0 z-10 m-3 mx-auto flex h-min justify-center gap-2 rounded-full"
		>
			{#each imgs as _, i}
				<span
					class="inline-block h-2 w-2 rounded-full bg-red sm:h-4 sm:w-4 {i != curr
						? 'opacity-35'
						: 'opacity-65'}"
				></span>
			{/each}
		</div>
	{/if}
</div>
