<!-- Beamer.svelte -->
<script lang="ts">
	import type { Snippet } from 'svelte';

	let { children, img }: { children: Snippet; img: string | null } = $props();
</script>

<div
	class="flex flex-col items-center justify-between gap-10 p-10 text-center even:bg-red even:text-white lg:h-1/2 lg:flex-row lg:gap-10 lg:text-left lg:even:flex-row-reverse lg:even:text-right xl:gap-0 xl:p-0"
>
	{#if img !== null}
		<img class="lg:h-full lg:w-auto lg:max-w-1/2" src={img} alt="img" />
	{/if}
	<div class="w-full text-lg lg:text-xl xl:p-10 xl:text-2xl">
		{@render children()}
	</div>
</div>
