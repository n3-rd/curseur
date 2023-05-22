<script>
	import { onMount } from 'svelte';

	const baseSize = 20;
	export let size = 20;
	export let color = 'black';
	export let shape = 'circle';
	export let mixBlendMode = 'none';

	let x = -100;
	let y = -100;

	onMount(() => {
		/**
		 * initialises the cursor
		 *
		 */
		const initCursor = () => {
			document.addEventListener('mousemove', (e) => {
				x = e.clientX;
				y = e.clientY;
			});
			const hoverables = document.querySelectorAll('.hoverable, a, button');
			hoverables.forEach((hoverable) => {
				hoverable.addEventListener('mouseenter', () => {
					size += 20;
					document.body.style.cursor = 'none';
				});
				hoverable.addEventListener('mouseleave', () => {
					size -= 20;
				});
			});
		};

		initCursor();
	});
</script>

<div class="cursor-wrapper" style="--x:{x}px; --y:{y}px">
	<div
		class="custom-cursor {shape}"
		style="transform: translate(-50%, -50%) scale({size / baseSize}); width: {baseSize}px; height: {baseSize}px; --mix-blend-mode: {mixBlendMode}; --background-color: {color}"
	/>
</div>

<style>
	.cursor-wrapper {
		--x: -100px;
		--y: -100px;
		position: fixed;

		left: 0;
		top: 0;
		transform: translate(var(--x), var(--y));
		pointer-events: none;
		cursor: none;
	}
	.custom-cursor {
		--background-color: 'black';
		--mix-blend-mode: 'none';
		left: 50%;
		top: 50%;

		background-color: var(--background-color);
		mix-blend-mode: var(--mix-blend-mode);
		border-radius: 50%;
		z-index: 99999;
		/* Customize your cursor styles here */
		transition: transform 0.2s cubic-bezier(0.28, 0.8, 0.36, 1);
	}

	.custom-cursor.square {
		border-radius: 0;
	}
	.cursor-none {
		cursor: none;
	}
</style>
