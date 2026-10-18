<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<!-- TODO: add header row -->
<main
	class="container mx-auto flex h-full
  min-h-screen flex-col items-center justify-center px-8 py-6"
>
	{@render children()}
</main>
