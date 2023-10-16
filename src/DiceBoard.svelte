<script lang="ts">
  import {
    AmbientLight,
    AnimationMixer,
    Group,
    Clock,
    DirectionalLight,
    LinearToneMapping,
    LoopOnce,
    OrthographicCamera,
    Scene,
    Vector3,
    Matrix4,
    GridHelper,
    WebGLRenderer,
  } from 'three';

  import { GLTFLoader } from 'three/addons/loaders/GLTFLoader';
  import type { GLTF } from 'three/addons/loaders/GLTFLoader';

  import { onMount } from 'svelte';

  // Data
  let sceneModel: GLTF;
  let mixer;
  let rollAnimation;
  let defaultQuaternion;
  let preloading = true;
  let rolling = false;
  let rotation = false;
  let edge = 1;

  const maxWidth = 380;
  const width = (window.innerWidth > maxWidth)
    ? maxWidth
    : window.innerWidth - 32
  const height = width;
  const dimension = 1;

  let clock = new Clock();
  const scene = new Scene();
  const camera = new OrthographicCamera(-dimension, dimension, dimension, -dimension, 0.01, 900);

  camera.position.y = 1;
  camera.lookAt(new Vector3(0, 0, 0));

  // Lighting
  // const punctualLights = true;
  const exposure = 0.0;
  const toneMapping = LinearToneMapping;
  const ambientIntensity = 0.7;
  const ambientColor = '#FFFFFF';
  const directIntensity = 1.8 * Math.PI;
  const directColor = '#FFFFFF';

  // Renderer
  const rendererConfig = {
    antiAlias: true,
    alpha: true,
  };
  const renderer = new WebGLRenderer(rendererConfig);
  renderer.setSize(width, height);
  if (window?.devicePixelRatio) {
    renderer.setPixelRatio(window.devicePixelRatio);
  }
  renderer.toneMapping = Number(toneMapping);
  renderer.toneMappingExposure = Math.pow(2, exposure);

  // Light 1 Ambient
  const light1 = new AmbientLight(ambientColor, ambientIntensity);
  light1.name = 'ambient_light';
  camera.add(light1);
  scene.add(light1);

  // Light 2 Directional
  const light2 = new DirectionalLight(directColor, directIntensity);
  // light2.position.set(1.5, 1, 0.866); // ~60º
  light2.position.set(1.2, 1.2, -1.4); // ~60º
  light2.name = 'main_light';
  camera.add(light2);
  scene.add(light2);

  let basePosition;
  const edgeSet = {
    1: {x: 1.1, y: -0.1, z: 0.8},
    2: {x: -0.8, y: -3, z: 0.2},
    3: {x: 1, y: 0.3, z: -0.3},
    4: {x: 4.2, y: 2.9, z: -0.4},
    5: {x: 2.8, y: 0, z: 1.3},
    6: {x: -0.65, y: 0.8, z: -3.6},
    7: {x: -1, y: 3.4, z: -2.9},
    8: {x: 0, y: 2.5, z: 0.8},
    9: {x: 2.4, y: 2.4, z: 3},
    10: {x: 0.1, y: -3.1, z: 1.1},
    11: {x: 3.8, y: 1.3, z: 0.6},
    12: {x: 0.18, y: -2.5, z: 0.25},
    13: {x: 3.9, y: 0.28, z: 0.45},
    14: {x: 0.2, y: -0, z: 3.2},
    15: {x: -6.3, y: 3.8, z: -2.9},
    16: {x: 2.4, y: 3.0, z: 0.9},
    17: {x: -2.8, y: 4.1, z: -3.8},
    18: {x: -5.2, y: 5.7, z: -3.5},
    19: {x: 0, y: 0, z: 0},
    20: {x: -2, y: 3.2, z: 0.8},
  }

  // Grid
  scene.add(new GridHelper(5, 30));
  const loader = new GLTFLoader();

  // Lifecycle
  const render = () => {
    requestAnimationFrame(render);
    if (mixer) {
      const delta = clock.getDelta();
      mixer.update(delta);
    }
    renderer.render(scene, camera);
  };

  /**
   * on Roll dice click
   */
  const onRollDice = () => {
    if (rolling) {
      return;
    }
    rotation = false;
    setEdge();
    prepareAnimation();
    render();
  };

  const setEdge = () => {
    const group = sceneModel.children[0];
    basePosition = !basePosition
      ? group.children[0].quaternion.clone()
      : basePosition;
    group.children[0].quaternion.copy(basePosition);
    edge = Math.ceil(Math.random() * (20 - 1) + 1);
    const set  = edgeSet[edge];
    console.log(edge)
    group.children[0].rotateX(set.x);
    group.children[0].rotateY(set.y);
    group.children[0].rotateZ(set.z);
  }

  const prepareAnimation = () => {
    const time =  9.3;
    // const time =  1;
    rolling = true;
    mixer = new AnimationMixer(sceneModel);
    const anim = rollAnimation[1];
    const action = mixer.clipAction(anim).setDuration(time);
    action.clampWhenFinished = true;
    action.setLoop(LoopOnce);
    action.play();
    setTimeout(() => {rolling = false}, (time * 1000) - 500);
  };

  onMount(() => {
    // renderer.render(scene, camera);
    const diceBoard = document.getElementById('dice-board');
    if (diceBoard) {
      diceBoard.appendChild(renderer.domElement);

      //  TODO: define device to choose model size
      loader.load('/glb-models/dice6.glb', function (gltf) {
        preloading    = false;
        rollAnimation = gltf.animations;
        sceneModel    = gltf.scene;
        const scale = 1.001;

        sceneModel.position.set(0, 0, 0.6);
        const baseDice = sceneModel.children[1];
        sceneModel.children = [baseDice];

        scene.add(sceneModel);
        renderer.render(scene, camera);
        rotation = true;
      });
    }
  });
</script>

<div class="h-fit w-fit mx-auto" id="dice-board" />

<footer class="absolute top-1/2 inset-x-0 bottom-4 text-center z-40">
<!-- <footer class="absolute top-[99.6%] inset-x-0 bottom-4 text-center z-40">  -->
  <button
    class="primary-button p-0.5 rounded-2xl"
    disabled={rolling}
    on:click={onRollDice}
  >
    <span class="primary-button-inner inline-block font-semibold w-48 py-2.5 rounded-2xl">
      {rolling ? `edge ${edge}` : "ROLL THE DICE"}
    </span>
  </button>
</footer>

<style>
.primary-button {
  background: linear-gradient(95.42deg, #FCD161 -15.22%, #E63801 115.22%);
}

.primary-button-inner {
  background: linear-gradient(180deg, #00386C 0%, #121212 100%);
  color: #F0AB00;
}
</style>
