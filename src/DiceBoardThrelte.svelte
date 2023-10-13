<script lang="ts">
  import { Canvas, T, useFrame, useLoader, forwardEventHandlers, useThrelte   } from '@threlte/core';
  import { Grid, interactivity } from '@threlte/extras'
  import { GLTFLoader } from 'three/addons/loaders/GLTFLoader';

  let rolling = false
  const dimension = 1;
  const gltf = useLoader(GLTFLoader).load('/glb-models/dice1_1024.glb')
  const directLight = {
    color: '#FFFFFF',
    intensity: 1.8 * Math.PI,
    position: [1.2, 1.2, -1.4],
  }
  const ambientLight = {
    intensity:  0.7,
    color: '#FFFFFF',
  }

  const { invalidate } = useThrelte()
  const el = document.getElementById('int-target')
  const component = forwardEventHandlers()

  let rotation = 0
  useFrame((state, delta) => {
    rotation += delta
  })

  const onCameraCreate = (event: CustomEvent) => {
    const { ref } = event;
    ref.near  = 0.01;
    ref.far   = 900;

    ref.left = -dimension;
    ref.right = dimension;
    ref.top = dimension;
    ref.bottom = -dimension;
    ref.position.y = 1;
    // ref.lookAt(0, 0, 0);
    console.log(ref)
  }

  const onDirectionalLightCreate = (event: CustomEvent) => {
    const { ref } = event;
  }
</script>
<T.OrthographicCamera
  zoom={80}
  position={[10, 10, 10]}
  makeDefault
  let:ref
>

<T.AmbientLight intensity={ambientLight.intensity} color={ambientLight.color} />
<T.DirectionalLight
  color={directLight.color}
  position={directLight.position}
  intensity={directLight.intensity}
  on:create={onDirectionalLightCreate}
/>
<!--<T.PerspectiveCamera-->
<!--    makeDefault-->
<!--    position={[10, 10, 10]}-->
<!--    on:create={({ ref }) => {-->
<!--    ref.lookAt(0, 1, 0)-->
<!--  }}-->
<!--/>-->

{#if $gltf}
  <T is={$gltf.scene} scale={3} />
{/if}
</T.OrthographicCamera>

<Grid
  position.y={-0.001}
  cellColor="#ffffff"
  sectionColor="#ffffff"
  sectionThickness={0}
  fadeDistance={25}
  cellSize={2}
/>

