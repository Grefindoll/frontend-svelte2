<script>
	let { text, color = 'blue' } = $props();

	const colors = {
		blue: 'bg-blue-100 text-blue-700 border-blue-200',
		green: 'bg-green-100 text-green-700 border-green-200',
		purple: 'bg-purple-100 text-purple-700 border-purple-200'
	};
</script>

<span
	class="inline-flex items-center px-3 py-1 rounded-full text-xs font-semibold border {colors[
		color
	]}"
>
	{text}
</span>
