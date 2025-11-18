<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
	import "../app.css";
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<a class="block bg-red-100 w-full" href="/">ホームに戻る</a>
{@render children()}
