<script>
	let { children, class: className = '', bg = 'white', fullScreen = false } = $props();

	const bgClass = bg === 'gray' ? 'bg-slate-50' : 'bg-white';

	// fullScreenがtrueの場合、min-h-screenを適用し、コンテンツを中央に配置するflexboxを追加
	// Headerの高さ分、コンテンツが上に隠れるのを防ぐため、pt-24を確保します。
	const heightClass = fullScreen ? 'min-h-screen flex items-center pt-24' : '';
</script>

<section class="{bgClass} py-16 sm:py-24 relative overflow-hidden {className} {heightClass}">
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 w-full">
		{@render children()}
	</div>
</section>
