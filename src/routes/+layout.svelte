<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';
	import { resolve } from '$app/paths';

	let { children } = $props();
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<div class="flex min-h-screen flex-col">
	<header class="border-b border-subtle py-6">
		<div class="mx-auto w-full max-w-2xl px-6">
			<a href={resolve('/')} class="font-mono text-sm tracking-tight text-ink">Cooper Glavin</a>
		</div>
	</header>

	<main class="flex-1 py-16">
		{@render children()}
	</main>

	<footer class="border-t border-subtle py-6">
		<div class="mx-auto w-full max-w-2xl px-6">
			<p class="font-mono text-xs text-muted">
				<a href="https://github.com/cglavin50" target="_blank" class="hover:text-accent">github</a>
				<a
					href="https://www.linkedin.com/in/cooper-glavin-5852351aa/"
					target="_blank"
					class="hover:text-accent">linkedin</a
				>
			</p>
		</div>
	</footer>
</div>
