<!-- Beamer.svelte -->
<script lang="ts">
	import type { Snippet } from 'svelte';
	import Caroussel from './Caroussel.svelte';

	let { children, imgs }: { children: Snippet; imgs: string[] | null } = $props();
</script>

<div
	class="flex flex-col items-center justify-between gap-10 p-10 text-center even:bg-red even:text-white lg:h-1/2 lg:flex-row lg:gap-15 lg:p-15 lg:text-left lg:even:flex-row-reverse lg:even:text-right"
>
	{#if imgs !== null}
		<Caroussel {imgs} />
	{/if}
	<div class="w-full text-lg lg:text-xl xl:p-10 xl:text-2xl">
		{@render children()}
	</div>
</div>
