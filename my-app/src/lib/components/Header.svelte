<script>
	import { onMount } from 'svelte';
	import Button from './Button.svelte';

	let { title = 'Light Corp' } = $props();
	let isMenuOpen = $state(false);
	let isScrolled = $state(false);

	const navItems = [
		{ label: 'Product', href: '/product' },
		{ label: 'Features', href: '/features' },
		{ label: 'Pricing', href: '/pricing' }
	];

	onMount(() => {
		const handleScroll = () => (isScrolled = window.scrollY > 20);
		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});
</script>

<header
	class="fixed top-0 w-full z-50 transition-all duration-500 {isScrolled
		? 'bg-white/80 backdrop-blur-xl border-b border-slate-200/60 py-3'
		: 'bg-transparent py-5'}"
>
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex justify-between items-center">
		<a
			href="/"
			class="text-2xl font-black tracking-tighter text-slate-900 flex items-center gap-2 z-50"
		>
			<div
				class="w-8 h-8 bg-gradient-to-br from-primary to-purple-600 rounded-lg shadow-lg shadow-indigo-500/30"
			></div>
			{title}
		</a>

		<nav class="hidden md:flex items-center gap-8">
			{#each navItems as item}
				<a
					href={item.href}
					class="text-sm font-medium text-slate-600 hover:text-primary transition-colors"
				>
					{item.label}
				</a>
			{/each}
			<div class="pl-4 border-l border-slate-200">
				<a href="/contact"
					><Button variant="primary" class="!py-2 !px-5 !text-sm">Get Started</Button></a
				>
			</div>
		</nav>

		<button onclick={() => (isMenuOpen = !isMenuOpen)} class="md:hidden p-2 text-slate-600 z-50">
			<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
				<path
					stroke-linecap="round"
					stroke-linejoin="round"
					stroke-width="2"
					d={isMenuOpen ? 'M6 18L18 6M6 6l12 12' : 'M4 6h16M4 12h16M4 18h16'}
				/>
			</svg>
		</button>

		{#if isMenuOpen}
			<div
				class="fixed inset-0 bg-white z-40 flex flex-col pt-24 px-6 space-y-6 animate-fade-in md:hidden"
			>
				{#each navItems as item}
					<a
						href={item.href}
						onclick={() => (isMenuOpen = false)}
						class="text-2xl font-bold text-slate-900"
					>
						{item.label}
					</a>
				{/each}
				<hr class="border-slate-100" />
				<a
					href="/contact"
					onclick={() => (isMenuOpen = false)}
					class="w-full py-4 bg-primary text-white text-center rounded-xl font-bold text-lg"
				>
					Get Started Free
				</a>
			</div>
		{/if}
	</div>
</header>
