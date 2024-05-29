<script lang="ts">
	import { T, Canvas } from '@threlte/core';
	import Zeus from './models/zeus.svelte';
	import { OrbitControls } from '@threlte/extras';
	import Scene from './Scene.svelte';

	const camera = {
		makeDefault: true,
		position: [10, 10, 10],
		zoom: 40
	};
</script>

<Canvas>
	<Scene />
</Canvas>
