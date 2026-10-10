<!-- Beamer.svelte -->
<script lang="ts">
	import type { Snippet } from 'svelte';
	import Caroussel from './Caroussel.svelte';

	let { children, imgs }: { children: Snippet; imgs: string[] | null } = $props();
</script>

<div
	class="flex flex-col items-center justify-between gap-10 p-5 text-center md:flex-row md:text-left md:even:flex-row-reverse md:even:text-right lg:gap-15 lg:p-15"
>
	{#if imgs !== null}
		<Caroussel {imgs} />
	{/if}
	<div class="w-full text-lg lg:text-xl xl:p-10 xl:text-2xl">
		{@render children()}
	</div>
</div>
