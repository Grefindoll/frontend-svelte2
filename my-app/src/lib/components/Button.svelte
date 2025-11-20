<script>
	let { children, type = 'button', variant = 'primary', class: className = '' } = $props();

	const base =
		'inline-flex items-center justify-center px-6 py-3 text-base font-medium rounded-full transition-all duration-300 transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-offset-2 cursor-pointer';

	const variants = {
		primary: 'text-white bg-primary hover:bg-primary-hover shadow-lg shadow-indigo-500/30',
		secondary:
			'text-slate-700 bg-white border border-slate-200 hover:bg-slate-50 hover:border-slate-300 shadow-sm',
		ghost: 'text-primary hover:bg-indigo-50'
	};
</script>

<button {type} class="{base} {variants[variant]} {className}">
	{@render children()}
</button>
