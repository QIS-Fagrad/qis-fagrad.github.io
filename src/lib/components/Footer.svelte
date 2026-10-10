<!-- Footer.svelte -->

<script lang="ts">
	import { Envelope, Linkedin } from '@boxicons/svelte';
</script>

<footer class="relative flex w-full flex-col items-center justify-around gap-5 bg-red text-white">
	<div class="flex h-min flex-row gap-5 pt-5">
		<a class="h-min" href="https://www.linkedin.com/company/quantum-information-science/"
			><Linkedin class="text-white" size="md" /></a
		>
		<a class="h-min" href="mailto:QIS-fagraad@math.ku.dk"
			><Envelope class="text-white" size="md" /></a
		>
	</div>
	<div class="text-center">
		&copy; 2026 Quantum Information Science Student Association - All Rights Reserved.
	</div>
</footer>
