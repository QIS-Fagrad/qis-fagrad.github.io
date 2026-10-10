<!-- Footer.svelte -->

<script lang="ts">
	import { Envelope, Github, Linkedin } from '@boxicons/svelte';
</script>

<footer class="relative flex w-full flex-col items-center justify-around bg-red text-white">
	<div class="flex h-min flex-row gap-5 py-5">
		<a class="h-min" href="https://www.github.com/qis-fagrad"
			><Github class="text-white" size="md" /></a
		>
		<a class="h-min" href="https://www.linkedin.com/company/quantum-information-science/"
			><Linkedin class="text-white" size="md" /></a
		>
		<a class="h-min" href="mailto:QIS-fagraad@math.ku.dk"
			><Envelope class="text-white" size="md" /></a
		>
	</div>
	<div class="px-3 pb-1 text-center text-sm">
		&copy; 2026 Quantum Information Science Student Association - All Rights Reserved.
	</div>
	<div class="px-3 pb-1 text-center text-sm">
		No generative AI was used in any extent in the creation of this website.
	</div>
</footer>
