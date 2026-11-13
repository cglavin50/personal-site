<script lang="ts">
	import { onMount } from 'svelte';
	import PortraitCard from '$lib/components/PortraitCard.svelte';

	type Theme = 'light' | 'dark';

	// default to light, <head> handles flickering
	// low risk, we aren't overriding this is just used for initial render of the icon anyways
	let theme: Theme = $state('light');
	onMount(() => {
		theme = (document.documentElement.getAttribute('data-theme') as Theme) ?? 'light';
	});

	function setTheme(next: Theme) {
		document.documentElement.setAttribute('data-theme', next);
		localStorage.setItem('theme', next);
		theme = next;
	}

	function toggleTheme() {
		setTheme(document.documentElement.getAttribute('data-theme') === 'dark' ? 'light' : 'dark');
	}
</script>

<div class="mx-3xl flex justify-between px-6">
	<!-- TODO: fix spacing to make image a little shorter  -->
	<div class="mx-auto mb-auto flex grow-2 flex-col gap-8 px-6 text-lg">
		<!-- TODO: add accent color -->
		<h1 class="w-full min-w-20 text-3xl tracking-tight text-accent">Hi, I'm Cooper</h1>
		<p>
			I'm a software engineer at <a
				href="https://www.citian.co/about"
				target="_blank"
				class="text-accent">Citian</a
			>, building systems to help improve pedestrian accessibility and improve local infrastructure.
		</p>
		<p>
			I work end-to-end: fullstack <strong>(TypeScript, Go)</strong>, infrastructure
			<strong>(OpenTofu/Terraform, CDK)</strong>, and the system design and engineering workflows
			that tie projects together.
		</p>

		<p>
			I care about implementing AI in a secure, responsible, and maintainable way that empowers
			developers to produce better software.
		</p>

		<div class="flex gap-4">
			<a
				target="_blank"
				aria-label="github link"
				href="https://github.com/cglavin50"
				class="transition-transform duration-300 hover:scale-110"
			>
				<span class="icon-[ant-design--github-filled]"></span>
			</a>

			<a
				target="_blank"
				aria-label="linkedin link"
				href="https://www.linkedin.com/in/cooper-glavin-5852351aa/"
				class="transition-transform duration-300 hover:scale-110"
			>
				<span class="icon-[ant-design--linkedin-filled]"></span>
			</a>

			<button
				class="transition-transform duration-300 hover:scale-110"
				aria-label="toggle contrast mode"
				onclick={() => {
					toggleTheme();
				}}
			>
				{#if theme === 'light'}
					<span class="icon-[ant-design--moon-outlined]"></span>
				{:else}
					<span class="icon-[ant-design--sun-filled]"></span>
				{/if}
			</button>
		</div>
	</div>
	<!-- TODO: figure out appropriate values for sizes -->
	<PortraitCard class="ml-auto w-4/5" />
</div>

<!-- TODO: add light/dark mode button (next to my name, or badges) -->
