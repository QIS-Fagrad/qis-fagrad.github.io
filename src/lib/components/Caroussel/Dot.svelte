<!--- Dot.svelte --->

<script lang="ts">
	const {
		small = $bindable(false),
		selected = $bindable(false)
	}: { small: boolean; selected: boolean } = $props();

	const size = small ? 1 : 2;
	const sm_size = small ? 2 : 4;
</script>

<span
	class="h-{size} w-{size} rounded-full bg-red transition sm:h-{sm_size} sm:w-{sm_size}
    {selected ? 'opacity-65 ' : 'opacity-35'}
    "
></span>
