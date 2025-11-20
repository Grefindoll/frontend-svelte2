<script>
	import Section from '$lib/components/Section.svelte';
	import ContactForm from '$lib/components/ContactForm.svelte';
</script>

<div class="bg-slate-50 min-h-screen pt-20">
	<Section>
		<div class="max-w-2xl mx-auto">
			<div class="text-center mb-12">
				<h1 class="text-4xl font-bold text-slate-900 mb-4">Get in Touch</h1>
				<p class="text-lg text-slate-600">
					プロジェクトのご相談、お見積もり、技術的な質問など、<br />お気軽にお問い合わせください。
				</p>
			</div>

			<ContactForm />
		</div>
	</Section>
</div>
