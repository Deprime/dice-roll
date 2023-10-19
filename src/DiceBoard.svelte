<script lang="ts">
  import { onMount } from 'svelte';
  import {
    AmbientLight,
    AnimationMixer,
    Clock,
    DirectionalLight,
    LinearToneMapping,
    LoopOnce,
    OrthographicCamera,
    Scene,
    Vector3,
    GridHelper,
    WebGLRenderer,
  } from 'three';

  import { GLTFLoader } from 'three/addons/loaders/GLTFLoader';
  import type { GLTF } from 'three/addons/loaders/GLTFLoader';

  import { EDGES, ROLL_POSITION } from './constants';

  // Data
  let sceneModel: GLTF;
  let mixer;
  let rollAnimation;
  let basePosition;
  let preloading = true;
  let rolling = false;
  let rotation = false;
  let finished = false;
  let edge: number|null = 1;

  // Animation and edge rotation timings
  let moment_percent = 0.28
  let time = 9.3;
  // let time = 1;
  const rotate_moment = time * moment_percent;

  const maxWidth = 380;
  const width = (window.innerWidth > maxWidth)
    ? maxWidth
    : window.innerWidth - 32
  const height = width;
  const dimension = 1;
  // const dimension = 1;

  let clock = new Clock();
  const scene = new Scene();
  const camera = new OrthographicCamera(-dimension, dimension, dimension, -dimension, 0.01, 900);

  camera.position.y = 1;
  camera.position.x = 0;
  camera.position.z = 0;
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

  // Grid
  // scene.add(new GridHelper(5, 30));
  const loader = new GLTFLoader();

  function bezier(t: number, initial: number, p1: number, p2: number, final: number){
    return (1 - t) * (1 - t) * (1 - t) * initial
      + 3 * (1 - t) * (1 - t) * t * p1
      + 3 * (1 - t) * t * t * p2
      + t * t * t * final;
  }


  // Lifecycle
  const zLim = 0.7
  const render = () => {
    requestAnimationFrame(render);
    if (mixer) {
      const delta = clock.getDelta();

      if (mixer.time >= rotate_moment && !rotation) {
        setEdge();
        rotation = true;
      }

      if (rotation && (sceneModel.position.x < 0.5 || sceneModel.position.z < zLim)) {
      // if (finished && !rolling && (sceneModel.position.x < 0.5 || sceneModel.position.z < zLim)) {
        console.log('anim')
        const x = sceneModel.position.x;
        let inc = x <= 0.1 ? delta : delta;
        inc = x <= 0.05 ? delta/5 : inc;
        inc = x > 0.05 &&  x <= 0.1 ? delta/4 : inc;
        inc = x > 0.1  &&  x <= 0.2 ? delta/3 : inc;
        inc = x > 0.2  &&  x <= 0.3 ? delta/2.5 : inc;
        inc = x > 0.3  &&  x <= 0.4 ? delta/3 : inc;
        inc = x > 0.4 ? delta/4 : inc;
        let zInc = inc / 5

        sceneModel.position.x = sceneModel.position.x + inc >= 0.5
          ? sceneModel.position.x = 0.5
          : sceneModel.position.x += inc;

        sceneModel.position.z = sceneModel.position.z - zInc >= zLim
          ? sceneModel.position.z = zLim
          : sceneModel.position.z += zInc;

        if (sceneModel.position.x === 0.5 && sceneModel.position.z === zLim) {
          console.log(sceneModel.position.x, sceneModel.position.y, sceneModel.position.z)
          finished = false;
        }
      }
      mixer.update(delta);
    }
    renderer.render(scene, camera);
  };

  /**
   * on Roll dice click
   */
  const onRollDice = ($$edge: number|null = null) => {
    if (rolling) {
      return;
    }
    rotation = false;
    edge = $$edge === null ? Math.ceil(Math.random() * (20 - 1) + 1) : $$edge;

    console.log(sceneModel.position.x, sceneModel.position.y, sceneModel.position.z)
    setRollPosition();
    console.log(sceneModel.position.x, sceneModel.position.y, sceneModel.position.z)

    prepareAnimation();
    render();
  };

  /**
   * Set position for rolling
   */
  const setRollPosition = () => {
    const group = sceneModel.children[0];
    group.children[0].quaternion.copy(basePosition);
    group.children[0].rotateX(ROLL_POSITION.x);
    group.children[0].rotateY(ROLL_POSITION.y);
    group.children[0].rotateZ(ROLL_POSITION.z);

    sceneModel.position.set(0, 0, 0.6);
  }

  /**
   * Set selected edge
   */
  const setEdge = () => {
    const group = sceneModel.children[0];
    group.children[0].quaternion.copy(basePosition);
    edge = edge === null
      ? Math.ceil(Math.random() * (20 - 1) + 1)
      : edge;
    const set = EDGES[edge];
    group.children[0].rotateX(set.x);
    group.children[0].rotateY(set.y);
    group.children[0].rotateZ(set.z);
  }

  const prepareAnimation = () => {
    rolling = true;
    mixer = new AnimationMixer(sceneModel);
    const anim = rollAnimation[1];
    const action = mixer.clipAction(anim).setDuration(time);
    action.clampWhenFinished = true;
    action.setLoop(LoopOnce);
    action.play();
    setTimeout(() => {
      rolling = false,
      finished = true;
    }, (time * 1000) - 500);
  };

  onMount(() => {
    const diceBoard = document.getElementById('dice-board');
    if (diceBoard) {
      diceBoard.appendChild(renderer.domElement);

      //  TODO: define device to choose model size
      loader.load('/glb-models/dice6.glb', function (gltf) {
        console.log(gltf);

        preloading    = false;
        rollAnimation = gltf.animations;
        sceneModel    = gltf.scene;

        // const scale = 1.001;
        sceneModel.position.set(0, 0, 0.6);

        const baseDice = sceneModel.children[1];
        sceneModel.children = [baseDice];

        const group = sceneModel.children[0];
        basePosition = group.children[0].quaternion.clone();
        scene.add(sceneModel);
        renderer.render(scene, camera);
        rotation = true;
      });
    }
  });
</script>

<div class="h-fit w-fit mx-auto" id="dice-board" />

<footer class="absolute bottom-4 md:bottom-auto md:top-1/2 inset-x-0 w-full px-4 text-center z-40">
  <div class="mb-4">
    <button
      class="primary-button p-0.5 rounded-2xl disabled:opacity-60 transition-all"
      disabled={rolling}
      on:click={() => onRollDice()}
    >
      <span class="primary-button-inner inline-block font-semibold w-48 py-2.5 rounded-2xl">
        {rolling ? `edge ${edge === null ? '...' : edge}` : "ROLL THE DICE"}
      </span>
    </button>
  </div>
  <div class="flex flex-wrap justify-center gap-1">
    {#each Object.keys(EDGES) as key}
      <button
        class="primary-button p-0.5 rounded-2xl disabled:opacity-60 transition-all"
        disabled={rolling}
        on:click={() => onRollDice(parseInt(key))}
      >
        <span class="primary-button-inner inline-block font-semibold w-fit px-4 py-2 rounded-2xl">
          {key}
        </span>
      </button>
    {/each}
  </div>
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
