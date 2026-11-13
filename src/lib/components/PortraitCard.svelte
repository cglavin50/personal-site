<script lang="ts">
	// The flip is driven purely by [data-theme] on <html>, which the head
	// script sets pre-paint, so the card renders correctly oriented with no
	// animation on initial load. Both faces stay in the DOM so the hidden one
	// is ready when the theme changes (no load flash on toggle).
	let { class: classProp = '' } = $props();
</script>

<div class="flip-scene aspect-2/3 {classProp}">
	<div class="flip-card">
		<div class="face face-front">
			<enhanced:img
				src="$lib/assets/cooper-apt-portrait.webp"
				alt="portrait of me"
				fetchpriority="high"
				class="h-full w-full rounded-xl border-6 border-accent object-cover"
			/>
		</div>
		<div class="face face-back">
			<enhanced:img
				src="$lib/assets/cooper-stair.webp"
				alt="portrait of me"
				fetchpriority="low"
				class="h-full w-full rounded-xl border-6 border-accent object-cover"
			/>
		</div>
	</div>
</div>

<style>
	.flip-scene {
		perspective: 1000px;
		transition: box-shadow 500ms ease;
	}

	.flip-card {
		position: relative;
		height: 100%;
		transform-style: preserve-3d;
		transition: transform 500ms ease;
		transform: translateY(0) rotateY(0);
	}

	.face {
		position: absolute;
		inset: 0;
		backface-visibility: hidden;
	}

	.face-back {
		transform: rotateY(180deg);
	}

	:global([data-theme='dark']) .flip-card {
		transform: rotateY(180deg);
	}

	@media (prefers-reduced-motion: reduce) {
		.flip-card {
			transition: none;
		}
	}
</style>
