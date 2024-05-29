<script lang="ts">
	import type * as THREE from 'three';
	import {
		T,
		type Props,
		type Events,
		type Slots,
		forwardEventHandlers,
		useTask
	} from '@threlte/core';
	import { Grid, OrbitControls, Text } from '@threlte/extras';
	import { interactivity, createTransition } from '@threlte/extras';
	interactivity();
	import Sharp from './models/sharp.svelte';
	import Gun from './models/gun.svelte';
	import type { Material } from 'three';

	let rotation = 0;
	useTask((delta) => {
		rotation += delta;
	});

	let knifeScale = 1;
	let gunScale = 1;
</script>

<T.PerspectiveCamera makeDefault position={[0, 0, 10]} fov={15}>
	<OrbitControls enableDamping />
</T.PerspectiveCamera>

<T.DirectionalLight intensity={10} position={[9, 10, 100]} />
<T.AmbientLight intensity={2} />
<!-- 
<Grid
	cellColor="#ffffff"
	sectionColor="#ffffff"
	sectionThickness={0}
	fadeDistance={25}
	cellSize={1}
/> -->

<Text text={'Couteau Fatal'} position={[0.3, 0.5, 0]} />

<Sharp
	on:pointerenter={() => (knifeScale = 2)}
	on:pointerout={() => (knifeScale = 1)}
	rotation.y={rotation}
	position={[0.7, 0, 0]}
	scale={knifeScale}
></Sharp>

<Text text={'Pistolet Zombie'} position={[-0.8, 0.5, 0]} />

<Gun
	on:pointerenter={() => (gunScale = 2)}
	on:pointerout={() => (gunScale = 1)}
	rotation.y={rotation}
	position={[-0.5, 0, 0]}
	scale={gunScale}
/>
