<script>
	import Button from './Button.svelte';
	let { title, subtitle } = $props();
</script>

<div class="relative pt-32 pb-20 lg:pt-48 lg:pb-32 overflow-hidden">
	<div class="absolute top-0 left-1/2 -translate-x-1/2 w-full h-full z-0 pointer-events-none">
		<div
			class="absolute top-20 left-0 w-[500px] h-[500px] bg-indigo-400/30 rounded-full mix-blend-multiply blur-3xl animate-pulse"
		></div>
		<div
			class="absolute top-40 right-0 w-[500px] h-[500px] bg-purple-400/30 rounded-full mix-blend-multiply blur-3xl animate-pulse"
			style="animation-delay: 2s"
		></div>
	</div>

	<div class="relative z-10 max-w-4xl mx-auto text-center px-4">
		<div
			class="inline-flex items-center px-3 py-1 rounded-full bg-indigo-50 text-primary text-sm font-semibold mb-8 border border-indigo-100 animate-fade-in"
		>
			<span class="mr-2">🚀</span> v2.0 is now available
		</div>

		<h1
			class="text-5xl lg:text-7xl font-black tracking-tight text-slate-900 mb-8 leading-[1.1] animate-slide-up"
		>
			{title}
			<span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-purple-600"
				>Reality.</span
			>
		</h1>

		<p
			class="text-xl text-slate-600 mb-10 max-w-2xl mx-auto leading-relaxed animate-slide-up"
			style="animation-delay: 0.1s"
		>
			{subtitle}
		</p>

		<div
			class="flex flex-col sm:flex-row justify-center gap-4 animate-slide-up"
			style="animation-delay: 0.2s"
		>
			<a href="/contact"><Button variant="primary">Start Building</Button></a>
			<a href="#features"><Button variant="secondary">Learn More</Button></a>
		</div>
	</div>
</div>
