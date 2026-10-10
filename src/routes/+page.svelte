<script lang="ts">
	import full_logo from '$lib/assets/red_full_logo.webp';
	import Beamer from '$lib/components/Beamer.svelte';
	import { CircleArrowDown, ArrowUp } from '@lucide/svelte';

	import { scrollTo, scrollRef } from 'svelte-scrolling';
	import { cubicInOut } from 'svelte/easing';
	import { setGlobalOptions } from 'svelte-scrolling';

	setGlobalOptions({
		duration: 500,
		offset: 0,
		easing: cubicInOut
	});

	let scrollY: number = $state(0);
	let innerHeight: number = $state(0);
	const cutoff = $derived(innerHeight * 0.9);

	const items = [
		{
			imgs: [
				'https://placehold.co/1920x1080',
				'https://placehold.co/1920x1080',
				'https://placehold.co/500x500',
				'https://placehold.co/1920x1080'
			],
			content: `
            We are an association of students from both the University of Copenhagen (KU)
            and the Technical University of Denmark (DTU) for Quantum Information Science.
            The association is overseen by the *QIS Fagråd*, the Student Council from the Master of Science
            in Quantum Information Science at both KU and DTU. Read more about us [here](/about-us).
		    `
		},

		{
			imgs: ['https://placehold.co/1920x1080'],
			content: `
            We oversee an *Academic Committee*, a *Social Commitee* and other initiatives. At these committees
            we focus on providing students with [events and opportunities](/events) to engage in both fun and learning experiences.
            Have an idea for an event you would like to see realised? Join our committees and will help with all
            organizational and funding concerns. The committees are open to any student at DTU or at KU's Faculty of Science.
		    `
		}
	];

	function render_md(text: string) {
		return text
			.replace(/\[(.+?)\]\((.+?)\)/g, "<a class='underline' href='$2'>$1</a>")
			.replace(/_(.+?)_/g, '<i>$1</i>')
			.replace(/\*(.+?)\*/g, '<b>$1</b>');
	}
</script>

<svelte:window bind:scrollY bind:innerHeight />
{#if scrollY > cutoff}
	<button
		use:scrollTo={'top'}
		class="bg-gray-200 fixed right-0 bottom-0 z-40 m-5 animate-fade-in rounded-full p-1.5 text-red shadow-black"
	>
		<ArrowUp class="size-5" stroke-width="3" />
	</button>
{:else}
	<button
		class="absolute right-0 bottom-0 left-0 z-40 mx-auto mb-4 flex justify-center lg:mb-7"
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

<div use:scrollRef={'content'} id="content">
	{#each items as { imgs, content }}
		<Beamer {imgs}>
			{@html render_md(content)}
		</Beamer>
	{/each}
</div>

<!-- {/each} -->
