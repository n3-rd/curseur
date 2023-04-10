<script>
	import { onMount } from 'svelte';

	export let size = 20;
	export let color = 'black';
	export let shape = 'circle';
	export let mixBlendMode = 'none';

	let x = -100;
	let y = -100;

	const cx = size / 2;
	const cy = size / 2;

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

<div
	class="custom-cursor {shape}"
	style="left: {x - cx}px; top: {y -
		cy}px;--size:{size}px; --mix-blend-mode: {mixBlendMode}; --background-color: {color}"
/>

<style>
	.custom-cursor {
		--background-color: 'black';
		--mix-blend-mode: 'none';
		--size: 20;
		background-color: var(--background-color);
		mix-blend-mode: var(--mix-blend-mode);
		width: var(--size);
		height: var(--size);
		position: fixed;
		border-radius: 50%;
		pointer-events: none;
		z-index: 99999;
		/* Customize your cursor styles here */
		transition: all 0.2s cubic-bezier(0.28, 0.8, 0.36, 1);
		cursor: none;
	}

	.custom-cursor.square {
		border-radius: 0;
	}
	.cursor-none {
		cursor: none;
	}
</style>
