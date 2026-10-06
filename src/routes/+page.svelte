<script lang="ts">
	import full_logo from '$lib/assets/red_full_logo.webp';
	import { ChevronsDown } from '@lucide/svelte';

	const lorem_ipsum =
		"Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since 1966, when designers at Letraset and James Mosley, the librarian at St Bride Printing Library in London, took a 1914 Cicero translation and scrambled it to make dummy text for Letraset's Body Type sheets. It has survived not only many decades, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised thanks to these sheets and more recently with desktop publishing software like Aldus PageMaker and Microsoft Word including versions of Lorem Ipsum";

	interface HomeItem {
		title: string;
		text: string;
		image_path: string;
	}

	const items: HomeItem[] = [
		{
			title: 'A title',
			text: lorem_ipsum,
			image_path: 'https://placehold.co/600x400'
		},
		{
			title: 'Another title',
			image_path: 'https://placehold.co/600x400',
			text: lorem_ipsum
		},
		{
			title: 'One more title',
			image_path: 'https://placehold.co/600x400',
			text: lorem_ipsum
		}
	];
</script>

<div class="flex h-dvh items-center justify-center">
	<img
		class="w-11/12 md:w-3/4 lg:w-1/2"
		src={full_logo}
		alt="Quantum Information Science Student Association"
	/>
	<a class="absolute bottom-0 mb-4 content-center lg:mb-7" href="#description" title="arrow-down">
		<ChevronsDown color="#901a1e" strokeWidth={3} class="size-8 lg:size-10" />
	</a>
</div>
<div class=""></div>

<div class="description" id="description"></div>
{#each items as { image_path, title, text }}
	<div class="img-text">
		<div>
			<h2>{title}</h2>
			<p>{text}</p>
		</div>
		<img src={image_path} alt="img" />
	</div>
{/each}

<style>
	.img-text {
		display: flex;
		justify-content: space-between;
		align-items: center;
		height: 50vh;
	}
	.img-text > img {
		height: 100%;
	}
	.img-text > div {
		width: 100%;
	}
	.img-text:nth-child(odd) {
		color: white;
		background-color: #901a1e;
	}
	.img-text:nth-child(even) {
		flex-direction: row-reverse;
	}
	.img-text > div {
		display: flex;
		flex-direction: column;
		padding: 2em 5em;
		align-content: center;
	}
	.img-text h2 {
		font-weight: bold;
		font-size: 1.8em;
		margin-bottom: 1em;
	}
	.img-text p {
		font-size: 1.1em;
	}
	@media screen and (height <= 800px) {
		.img-text {
			height: 100vh;
		}
	}
	@media screen and (width <= 1400px) {
		.img-text > img {
			height: auto;
			width: 40vw;
			padding: 2em;
		}
	}
	@media screen and (width <= 1000px) {
		.img-text:nth-child(odd),
		.img-text:nth-child(even) {
			display: flex;
			flex-direction: column;
		}
		.img-text {
			justify-content: space-between;
			align-items: center;
			height: min-content;
			padding: 2em auto;
		}
		.img-text > img {
			width: 100vw;
			padding: 0;
		}
		.img-text > div {
			padding: 1em 1em;
		}
	}
</style>
