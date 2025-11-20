<script>
	import { onMount } from 'svelte';

	let { title = 'Light Corp' } = $props();
	let isMenuOpen = $state(false);
	let isScrolled = $state(false);

	const navItems = [
		{ label: 'Product', href: '/product' },
		{ label: 'Solutions', href: '/solutions' },
		{ label: 'Pricing', href: '/pricing' },
		{ label: 'About', href: '/about' }
	];

	// スクロール検知
	function handleScroll() {
		isScrolled = window.scrollY > 20;
	}

	onMount(() => {
		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});
</script>

<header
	class="fixed top-0 w-full z-50 transition-all duration-300 border-b border-transparent
	{isScrolled
		? 'bg-white/80 backdrop-blur-md border-gray-200 shadow-sm py-2'
		: 'bg-transparent py-4'}"
>
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
		<div class="flex justify-between items-center">
			<a href="/" class="text-2xl font-black tracking-tighter text-accent flex items-center gap-2">
				<div class="w-8 h-8 bg-gradient-to-tr from-primary to-purple-500 rounded-lg"></div>
				{title}
			</a>

			<nav class="hidden md:flex items-center space-x-8">
				{#each navItems as item}
					<a
						href={item.href}
						class="text-sm font-medium text-gray-600 hover:text-primary transition-colors"
					>
						{item.label}
					</a>
				{/each}
				<a
					href="/contact"
					class="px-4 py-2 rounded-full bg-accent text-white text-sm font-bold hover:bg-gray-800 transition-transform hover:scale-105 shadow-lg shadow-gray-900/20"
				>
					Get Started
				</a>
			</nav>

			<button onclick={() => (isMenuOpen = !isMenuOpen)} class="md:hidden text-gray-600 p-2">
				<span class="sr-only">Menu</span>
				<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="2"
						d={isMenuOpen ? 'M6 18L18 6M6 6l12 12' : 'M4 6h16M4 12h16M4 18h16'}
					/>
				</svg>
			</button>
		</div>
	</div>

	{#if isMenuOpen}
		<div
			class="absolute top-full left-0 w-full bg-white/95 backdrop-blur-xl border-b border-gray-200 shadow-xl md:hidden animate-in slide-in-from-top-5"
		>
			<div class="p-4 space-y-4">
				{#each navItems as item}
					<a
						href={item.href}
						onclick={() => (isMenuOpen = false)}
						class="block text-lg font-medium text-gray-800 hover:text-primary"
					>
						{item.label}
					</a>
				{/each}
				<hr class="border-gray-100" />
				<a
					href="/contact"
					class="block text-center w-full py-3 bg-primary text-white rounded-lg font-bold"
				>
					Get Started Now
				</a>
			</div>
		</div>
	{/if}
</header>
