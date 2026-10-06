<!-- Nav.svelte -->
<script lang="ts">
	import logo from '$lib/assets/red_logo.webp';
	import { X, Menu } from '@lucide/svelte';

	import { page } from '$app/state';
	interface NavItem {
		href: string;
		label: string;
	}
	const navItems: NavItem[] = [
		{ href: '/', label: 'Home' },
		{ href: '/events', label: 'Events' },
		{ href: '/about-us', label: 'About Us' },
		{ href: '/contact-us', label: 'Contact Us' }
	];

	let { open = $bindable(false) }: { open: boolean } = $props();

	const toggle_open = () => {
		open = !open;
	};
	const close = () => {
		open = false;
	};
</script>

<nav class="fixed h-dvh w-dvw">
	<div class="flex h-min items-center justify-between bg-white px-5 py-3 lg:px-10 lg:py-5">
		<button
			class="m-1 h-min cursor-pointer items-center bg-transparent lg:hidden"
			onclick={toggle_open}
			aria-label="open-burguer-menu"
		>
			{#if open}
				<X color="#901a1e" strokeWidth={2} />
			{:else}
				<Menu color="#901a1e" strokeWidth={2.5} />
			{/if}
		</button>
		<div class="hidden w-min gap-10 lg:flex">
			{#each navItems as { href, label }}
				<a
					onclick={close}
					{href}
					class="h-min w-min cursor-pointer border-red p-2 text-center whitespace-nowrap text-red
                {page.url.pathname === href ? 'border-b-2 font-bold' : ''}"
					>{label}
				</a>
			{/each}
		</div>
		<a href="/" aria-label="home-logo" class="col-start-2 m-1 inline-flex h-10" onclick={close}>
			<img src={logo} alt="logo" /></a
		>
	</div>
	<div class="relative h-full">
		<div
			class="h-full w-full bg-white {open ? 'block' : 'hidden'} 
            absolute
            z-50
            animate-left-slide-in
            "
		>
			<div class="col-span-2 col-start-1 row-start-2 flex w-full flex-col items-center lg:hidden">
				{#each navItems as { href, label }}
					<a
						onclick={close}
						{href}
						class="w-full cursor-pointer border-t py-6 text-center text-red last:border-b hover:bg-red
                hover:text-white
                {page.url.pathname === href ? 'font-bold' : ''}"
						>{label}
					</a>
				{/each}
			</div>
		</div>
	</div>
</nav>
