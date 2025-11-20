<script>
	import Hero from '$lib/components/Hero.svelte';
	import Section from '$lib/components/Section.svelte';
	import Card from '$lib/components/Card.svelte';
	import Badge from '$lib/components/Badge.svelte';
</script>

<Hero
	title="Turn Ideas into"
	subtitle="Runesによるモダンな状態管理、Tailwind v4によるCSSファーストなスタイリング。最新技術の結晶で、あなたのWebサイト構築体験を一新します。"
/>

<Section id="features">
	<div class="text-center max-w-3xl mx-auto mb-16">
		<Badge text="Powerful Features" color="purple" />
		<h2 class="mt-6 text-3xl font-bold tracking-tight text-slate-900 sm:text-4xl">
			必要なものは、すべてここに。
		</h2>
		<p class="mt-4 text-lg text-slate-600">
			デザインからデプロイまで。開発者が本来のクリエイティビティを発揮できる環境を提供します。
		</p>
	</div>

	<div class="grid grid-cols-1 md:grid-cols-3 gap-8">
		<Card
			icon="⚡️"
			title="Lightning Fast"
			description="仮想DOMを使わないSvelteのコンパイラ技術により、驚異的なパフォーマンスを実現します。"
		/>
		<Card
			icon="🎨"
			title="Beautiful by Default"
			description="計算された余白、美しいタイポグラフィ。配置するだけで洗練されたデザインが完成します。"
		/>
		<Card
			icon="🛡️"
			title="Secure & Scalable"
			description="エンタープライズレベルのセキュリティ基準を満たし、ビジネスの成長に合わせてスケールします。"
		/>
	</div>
</Section>

<Section bg="gray">
	<div class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
		<div>
			<Badge text="Our Mission" color="blue" />
			<h2 class="mt-6 text-3xl font-bold text-slate-900 sm:text-4xl">複雑さをシンプルに。</h2>
			<p class="mt-4 text-lg text-slate-600 leading-relaxed">
				私たちのプラットフォームを使えば、複雑なインフラ管理から解放されます。
				直感的なインターフェースと強力なAPIで、開発のボトルネックを解消しましょう。
			</p>
			<ul class="mt-8 space-y-4">
				{#each ['直感的なダッシュボード', 'リアルタイムアナリティクス', '24時間365日のサポート'] as item}
					<li class="flex items-center text-slate-700 font-medium">
						<span
							class="w-6 h-6 rounded-full bg-green-100 text-green-600 flex items-center justify-center mr-3 text-xs font-bold"
							>✓</span
						>
						{item}
					</li>
				{/each}
			</ul>
		</div>
		<div class="relative">
			<div
				class="absolute inset-0 bg-gradient-to-r from-primary to-purple-600 rounded-2xl transform rotate-3 opacity-20 blur-lg"
			></div>
			<img
				src="https://placehold.co/800x600/f1f5f9/475569?text=Dashboard+UI"
				alt="Dashboard"
				class="relative rounded-2xl shadow-2xl border border-slate-200 transform -rotate-2 hover:rotate-0 transition-transform duration-500"
			/>
		</div>
	</div>
</Section>
