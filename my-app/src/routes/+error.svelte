<script>
	import { page } from '$app/stores';
	import Button from '$lib/components/Button.svelte';
	import Section from '$lib/components/Section.svelte';

	// ステータスコードによってメッセージを変える簡単なロジック
	// $derived ではなく、ストア($page)から直接読み取るだけでリアクティブに動作します
	let status = $derived($page.status);
	let message = $derived($page.error?.message || 'Unknown Error');

	const errorContent = {
		404: {
			title: '404',
			description: 'お探しのページは存在しないか、移動した可能性があります。',
			emoji: '🤔'
		},
		500: {
			title: '500',
			description: 'サーバー側で問題が発生しました。しばらく経ってから再度お試しください。',
			emoji: '😵'
		}
	};

	// 定義されていないエラーコードの場合はデフォルト表示
	let content = $derived(
		errorContent[status] || {
			title: 'Error Occurred',
			description: message,
			emoji: '⚠️'
		}
	);
</script>

<div class="flex items-center justify-center min-h-dvh">
	<Section>
		<div class="relative text-center max-w-2xl mx-auto z-10">
			<div
				class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 text-[12rem] sm:text-[20rem] font-black text-slate-100 z-[-1] select-none leading-none"
			>
				{status}
			</div>

			<div class="text-6xl mb-4 animate-bounce">
				{content.emoji}
			</div>

			<h1 class="text-4xl sm:text-5xl font-bold text-slate-900 mb-6">
				{content.title}
			</h1>

			<p class="text-lg text-slate-600 mb-10 leading-relaxed">
				{content.description}
			</p>

			<div class="flex justify-center gap-4">
				<a href="/">
					<Button variant="primary">ホームに戻る</Button>
				</a>
				<button onclick={() => history.back()}>
					<Button variant="secondary">前のページへ</Button>
				</button>
			</div>
		</div>

		<div
			class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-full max-w-3xl h-96 bg-linear-to-r from-indigo-100 to-purple-100 rounded-full mix-blend-multiply filter blur-3xl opacity-50 z-[-2] pointer-events-none"
		></div>
	</Section>
</div>
