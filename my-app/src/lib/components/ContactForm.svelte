<script>
	import Button from './Button.svelte';

	let formData = $state({ name: '', email: '', message: '' });
	let status = $state('idle'); // idle, submitting, success

	function handleSubmit(e) {
		e.preventDefault();
		status = 'submitting';

		// 送信シミュレーション
		setTimeout(() => {
			status = 'success';
		}, 1500);
	}
</script>

<div class="bg-white p-8 sm:p-10 rounded-2xl shadow-xl border border-slate-100">
	{#if status === 'success'}
		<div class="text-center py-16 animate-fade-in">
			<div
				class="w-16 h-16 bg-green-100 text-green-600 rounded-full flex items-center justify-center mx-auto mb-6 text-3xl"
			>
				✓
			</div>
			<h3 class="text-2xl font-bold text-slate-900 mb-2">Message Sent!</h3>
			<p class="text-slate-500">お問い合わせありがとうございます。</p>
		</div>
	{:else}
		<form onsubmit={handleSubmit} class="space-y-6">
			<div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
				<div>
					<label for="name" class="block text-sm font-semibold text-slate-700 mb-2">Name</label>
					<input
						type="text"
						id="name"
						bind:value={formData.name}
						required
						class="w-full px-4 py-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-primary focus:border-primary outline-none transition-all"
						placeholder="John Doe"
					/>
				</div>
				<div>
					<label for="email" class="block text-sm font-semibold text-slate-700 mb-2">Email</label>
					<input
						type="email"
						id="email"
						bind:value={formData.email}
						required
						class="w-full px-4 py-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-primary focus:border-primary outline-none transition-all"
						placeholder="john@example.com"
					/>
				</div>
			</div>

			<div>
				<label for="message" class="block text-sm font-semibold text-slate-700 mb-2">Message</label>
				<textarea
					id="message"
					rows="4"
					bind:value={formData.message}
					required
					class="w-full px-4 py-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-primary focus:border-primary outline-none transition-all"
					placeholder="How can we help?"
				></textarea>
			</div>

			<Button type="submit" class="w-full" disabled={status === 'submitting'}>
				{status === 'submitting' ? 'Sending...' : 'Send Message'}
			</Button>
		</form>
	{/if}
</div>
