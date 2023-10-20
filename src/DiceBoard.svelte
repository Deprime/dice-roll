<script lang="ts">
  import { onMount } from 'svelte';
  import {
    Scene,
    Clock,
    Vector3,
    LoopOnce,
    GridHelper,
    AmbientLight,
    WebGLRenderer,
    AnimationMixer,
    DirectionalLight,
    LinearToneMapping,
    OrthographicCamera,
  } from 'three';
  import { GLTFLoader } from 'three/addons/loaders/GLTFLoader';

  // Types
  import type { GLTF } from 'three/addons/loaders/GLTFLoader';
  import type {
    Mesh as IMesh,
    Group as IGroup,
    Quaternion as IQuaternion,
    AnimationClip as IAnimationClip,
    AnimationMixer as IAnimationMixer } from '@types/three';

  import type { IEdge } from './types';
  type TSceneChild = IGroup|IMesh;

  // Constants
  import { EDGES, ROLL_POSITION } from './constants';

  // Data
  let sceneModel: GLTF;
  let mixer: IAnimationMixer;
  let rollAnimation: IAnimationClip;
  let basePosition: IQuaternion;
  let preloading = true;
  let rolling = false;
  let rotation = false;
  let finished = false;
  let edge: number|null = 1;
  let meshes: TSceneChild[] = [];

  // Animation and edge rotation timings
  let moment_percent = 0.28
  // let animationDuration = 9.3;
  let animationDuration = 7;
  const rotate_moment = animationDuration * moment_percent;
  const maxWidth = 380;
  const width = (window.innerWidth > maxWidth)
    ? maxWidth
    : window.innerWidth - 32
  const height = width;
  const dimension = 1.08;

  let clock = new Clock();
  const scene = new Scene();
  const camera = new OrthographicCamera(-dimension, dimension, dimension, -dimension, 0.01, 1900);

  camera.position.y = 1;
  camera.position.x = 0;
  camera.position.z = 0;
  camera.lookAt(new Vector3(0, 0, 0));

  // Lighting
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
  camera.add(light1);
  scene.add(light1);

  // Light 2 Directional
  const light2 = new DirectionalLight(directColor, directIntensity);
  light2.position.set(1.2, 1.2, -1.4);
  camera.add(light2);
  scene.add(light2);

  // Grid
  scene.add(new GridHelper(5, 30));
  const loader = new GLTFLoader();

  // Methods
  /**
   * Render
   */
  // const zLim = 0.7
  const render = (): void  => {
    // if (finished) {
    //   return;
    // }
    requestAnimationFrame(render);
    const delta = clock.getDelta();

    if (mixer) {

      if (mixer.time >= rotate_moment && !rotation) {
        setEdge();
        rotation = true;
      }
      // if (rotation && (sceneModel.position.x < 0.5 || sceneModel.position.z < zLim)) {
      //   moveToCenter(delta)
      // }
      mixer.update(delta);
    }
    if (mixer.time + delta < animationDuration) {
      renderer.render(scene, camera);
    }
    else {
      rolling = false,
      finished = true;
    }
  };

  // const moveToCenter = (delta: number) => {
  //   const x = sceneModel.position.x;
  //   let inc = x <= 0.1 ? delta : delta;
  //   inc = x <= 0.05 ? delta/5 : inc;
  //   inc = x > 0.05 &&  x <= 0.1 ? delta/4 : inc;
  //   inc = x > 0.1  &&  x <= 0.2 ? delta/3 : inc;
  //   inc = x > 0.2  &&  x <= 0.3 ? delta/2.5 : inc;
  //   inc = x > 0.3  &&  x <= 0.4 ? delta/3 : inc;
  //   inc = x > 0.4 ? delta/4 : inc;
  //   let zInc = inc / 5

  //   sceneModel.position.x = sceneModel.position.x + inc >= 0.5
  //     ? sceneModel.position.x = 0.5
  //     : sceneModel.position.x += inc;

  //   sceneModel.position.z = sceneModel.position.z - zInc >= zLim
  //     ? sceneModel.position.z = zLim
  //     : sceneModel.position.z += zInc;

  //   if (sceneModel.position.x === 0.5 && sceneModel.position.z === zLim) {
  //     finished = false;
  //   }
  // }

  /**
   * On roll dice click
   */
  const onRollDice = ($$edge: number|null = null): void  => {
    if (rolling) {
      return;
    }
    rotation = false;
    edge = $$edge === null ? Math.ceil(Math.random() * (20 - 1) + 1) : $$edge;
    setRollPosition();
    prepareAnimation();
    render();
  };

  /**
   * Set position for rolling
   */
  const setRollPosition = (): void  => {
    const group = meshes[2];
    group.quaternion.copy(basePosition);
    group.rotateX(ROLL_POSITION.x);
    group.rotateY(ROLL_POSITION.y);
    group.rotateZ(ROLL_POSITION.z);
    sceneModel.position.set(0, 0, 0.6);
  }

  /**
   * Set selected edge
   */
  const setEdge = (): void  => {
    const group = meshes[2];
    group.quaternion.copy(basePosition);
    edge = edge === null
      ? Math.ceil(Math.random() * (20 - 1) + 1)
      : edge;
    const set = EDGES[edge] as IEdge;

    group.rotateX(set.x);
    group.rotateY(set.y);
    group.rotateZ(set.z);
  }

  const prepareAnimation = (): void => {
    finished = false;
    rolling = true;
    mixer = new AnimationMixer(sceneModel);
    const action = mixer.clipAction(rollAnimation).setDuration(animationDuration);
    action.clampWhenFinished = true;
    action.setLoop(LoopOnce, 1);
    action.play();
    console.log(action)

    // setTimeout(() => {
    //   rolling = false,
    //   finished = true;
    // }, (animationDuration * 1000) - 500);
  };

  onMount((): void  => {
    const diceBoard = document.getElementById('dice-board');
    if (diceBoard) {
      diceBoard.appendChild(renderer.domElement);

      loader.load('/glb-models/test26.glb', function (gltf: GLTF) {
        gltf.scene.traverse((child: TSceneChild) => {
          meshes.push(child)
        });

        rollAnimation = gltf.animations[0];
        sceneModel = gltf.scene;
        sceneModel.position.set(0, 0, 0.6);

        const scale = 0.55;
        meshes[1].scale.set(scale, scale, scale)
        basePosition = meshes[2].quaternion.clone();

        scene.add(sceneModel);
        renderer.render(scene, camera);

        preloading = false;
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
      disabled={rolling || preloading}
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
        disabled={rolling || preloading}
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
