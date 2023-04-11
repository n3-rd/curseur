<script>
	import Cursor from '$lib/Cursor.svelte';
	import { onMount, afterUpdate } from 'svelte';
	let cursorColor = 'green';
	let cursorSize = 28;
	let cursorSquare = false;
	let cursorMixBlendMode = 'exclusion';
	let cursorShape = 'circle';

	if (cursorSquare) {
		cursorShape = 'square';
	}

	onMount(() => {
		const cursorElement = document.querySelector('.cursor-element');
		const cursorOutput = document.querySelector('.cursor-output');
		if (cursorElement && cursorOutput) {
			cursorOutput.textContent =
				// format the output
				`<Cursor color="${cursorColor}" mixBlendMode="${cursorMixBlendMode}" size="${cursorSize}" />`;
		}
	});

	afterUpdate(() => {
		const cursorElement = document.querySelector('.cursor-element');
		const cursorOutput = document.querySelector('.cursor-output');
		if (cursorElement && cursorOutput) {
			cursorOutput.textContent =
				// format the output
				`<Cursor color="${cursorColor}" mixBlendMode="${cursorMixBlendMode}" size="${cursorSize}"  />`;
		}
	});
</script>

<div class="page">
	<!-- <h1>Welcome to your library project</h1>
	<p>Create your package using @sveltejs/package and preview/showcase your work with SvelteKit</p>
	<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p> -->

	<div class="title">Curseur</div>
	<div class="description">
		Svelte component for creating customizable cursors.

		<br />
		<a href="https://www.npmjs.com/package/curseur">Documentation</a>
		<a href="https://github.com/n3-rd/curseur">Github</a>
	</div>

	<div class="input-controls">
		<div>
			<label for="color">Color</label>
			<input type="text" bind:value={cursorColor} placeholder="Color" id="color" />
		</div>
		<div>
			<label for="size">Size</label>
			<input type="number" bind:value={cursorSize} placeholder="Size" id="size" />
		</div>
		<!-- use a select for mix-blend-mode -->
		<div>
			<label for="mix-blend-mode">Mix Blend Mode</label>
			<select bind:value={cursorMixBlendMode} id="mix-blend-mode">
				<option value="normal">Normal</option>
				<option value="multiply">Multiply</option>
				<option value="screen">Screen</option>
				<option value="overlay">Overlay</option>
				<option value="darken">Darken</option>
				<option value="lighten">Lighten</option>
				<option value="color-dodge">Color Dodge</option>
				<option value="color-burn">Color Burn</option>
				<option value="hard-light">Hard Light</option>
				<option value="soft-light">Soft Light</option>
				<option value="difference">Difference</option>
				<option value="exclusion">Exclusion</option>
				<option value="hue">Hue</option>
				<option value="saturation">Saturation</option>
				<option value="color">Color</option>
				<option value="luminosity">Luminosity</option>
			</select>
		</div>

		<div>
			<label for="square">Square</label>
			<input type="checkbox" bind:checked={cursorSquare} id="square" />
		</div>
	</div>
	<code class="cursor-output" />
	<div class="credits">
		Created with love by <a href="https://github.com/n3-rd">N3-rd (Jemegah Godwin)</a>
	</div>
</div>

<div class="cursor-element">
	<Cursor
		color={cursorColor}
		mixBlendMode={cursorMixBlendMode}
		size={cursorSize}
		shape={cursorSquare ? 'square' : 'circle'}
	/>
</div>

<style scoped>
	.page {
		font-family: 'Satoshi', sans-serif;
		margin: 2rem 2rem;
		min-height: 100vh;
		border-radius: 15px;
		background-color: #836bee;
		cursor: none;
	}

	a {
		cursor: none;
		color: #ffdada;
	}

	.title {
		font-size: 6rem;
		text-align: center;
		font-weight: 900;
		color: #fff;
	}

	.description {
		font-size: 1.5rem;
		text-align: center;
		color: #fff;
		padding: 2rem 2rem;
	}

	.input-controls {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 2rem 2rem;
		color: #fff;
		font-size: 1.5rem;
	}

	.cursor-output {
		font-size: 1.5rem;
		text-align: center;
		color: #fff;
		background: #000;
		display: flex;
		justify-content: center;
		align-items: center;
		padding: 1rem 2rem;
		border-radius: 10px;
		margin-top: 2rem;
	}

	.credits {
		font-size: 1.5rem;
		text-align: center;
		color: #fff;
		padding: 2rem 2rem;
	}
	.cursor-element {
		display: flex;
		justify-content: center;
		align-items: center;
	}
</style>
