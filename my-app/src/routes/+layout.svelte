<script>
	let { title = "MySite" } = $props();
</script>

<header>
	<div class="inner">
		<div class="logo"><a href="/">{title}</a></div>
		<nav>
			<a href="/">ホーム</a>
			<a href="/about">私たちについて</a>
			<a href="/contact">お問い合わせ</a>
		</nav>
	</div>
</header>

<style>
	header { background: #fff; border-bottom: 1px solid #eee; padding: 1rem 0; }
	.inner { max-width: 800px; margin: 0 auto; display: flex; justify-content: space-between; align-items: center; padding: 0 1rem; }
	.logo a { font-weight: bold; font-size: 1.2rem; text-decoration: none; color: #333; }
	nav a { margin-left: 1rem; text-decoration: none; color: #555; }
	nav a:hover { color: #007bff; }
</style>