<script>
	let { title, description, icon = null, image = null } = $props();
</script>

<div
	class="group relative bg-white rounded-2xl p-6 shadow-sm border border-slate-100 hover:shadow-xl hover:-translate-y-1 transition-all duration-300 overflow-hidden"
>
	{#if image}
		<div class="mb-6 -mx-6 -mt-6 h-48 overflow-hidden bg-slate-100">
			<img
				src={image}
				alt={title}
				class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700"
			/>
		</div>
	{/if}

	{#if icon}
		<div
			class="w-12 h-12 rounded-xl bg-indigo-50 text-primary flex items-center justify-center text-2xl mb-4 group-hover:rotate-12 transition-transform duration-300"
		>
			{icon}
		</div>
	{/if}

	<h3 class="text-xl font-bold text-slate-900 mb-3 group-hover:text-primary transition-colors">
		{title}
	</h3>
	<p class="text-slate-600 leading-relaxed">
		{description}
	</p>
</div>
