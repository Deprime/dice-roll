<script lang="ts">
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
    WebGLRenderer,
  } from 'three';
  import { GLTFLoader } from 'three/addons/loaders/GLTFLoader';
  import type { GLTF } from 'three/addons/loaders/GLTFLoader';

  import { onMount } from 'svelte';

  // Data
  let model: GLTF;
  let mixer;
  let rollAnimation;
  let defaultQuaternion;
  let preloading = true;
  let rolling = false;
  let rotation = false;

  const maxWidth = 350;
  const width = (window.innerWidth > maxWidth) 
    ? maxWidth
    : window.innerWidth
  const height = width;
  const dimension = 1.2;

  let clock = new Clock();
  const scene = new Scene();
  const camera = new OrthographicCamera(-dimension, dimension, dimension, -dimension, 0.01, 900);

  camera.position.y = 1;
  camera.lookAt(new Vector3(0, 0, 0));

  // Lighting
  // const punctualLights = true;
  const exposure = 0.0;
  const toneMapping = LinearToneMapping;
  // const ambientIntensity = 0.5;
  const ambientIntensity = 0.8;
  const ambientColor = '#FFFFFF';
  // const directIntensity = 1.2 * Math.PI;
  const directIntensity = 2.0 * Math.PI;
  const directColor = '#FFFFFF';

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

  const light1 = new AmbientLight(ambientColor, ambientIntensity);
  light1.name = 'ambient_light';
  camera.add(light1);
  scene.add(light1);

  const light2 = new DirectionalLight(directColor, directIntensity);
  // light2.position.set(1.5, 1, 0.866); // ~60º
  light2.position.set(1.2, 1.2, -1.4); // ~60º
  light2.name = 'main_light';
  camera.add(light2);
  scene.add(light2);

  const loader = new GLTFLoader();

  // Lifecycle
  const prepareAnimation = () => {
    model.position.set(0, 0, 0.4);

    const time = 10.5;
    rolling = true;
    mixer = new AnimationMixer(model);
    const action = mixer.clipAction(rollAnimation).setDuration(time);
    action.clampWhenFinished = true;
    action.setLoop(LoopOnce);
    action.play();

    setTimeout(() => {
      rolling = false
    }, (time * 1000) - 500 )
  };

  const render = () => {
    requestAnimationFrame(render);
    if (mixer) {
      mixer.update(clock.getDelta());
    }
    renderer.render(scene, camera);
  };

  const onPreview = () => {
    model.position.set(0, 0, 0);
    animatePreview();
  }

  const animatePreview = () => {
    if (!rotation) {
      return;
    }
    const angleX = 0.001;
    const angleY = 0.002;
    const angleZ = 0.001;
    
    requestAnimationFrame(animatePreview);
    model.rotateX(angleX);
    model.rotateY(angleY);
    model.rotateZ(angleZ);
    renderer.render(scene, camera);
  }

  const onRollDice = () => {
    if (rolling) {
      return;
    }
    rotation = false;
    model.quaternion.copy(defaultQuaternion);
    model.position.set(0, 0, 0.4);

    prepareAnimation();
    render();
  };

  onMount(() => {
    // renderer.render(scene, camera);
    const diceBoard = document.getElementById('dice-board');
    if (diceBoard) {
      diceBoard.appendChild(renderer.domElement);

      //  TODO: define device to choose model size
      loader.load('/glb-models/dice1_1024.glb', function (gltf) {
        preloading = false;
        rollAnimation = gltf.animations[0];
        model = gltf.scene;
        model.position.set(0, 0, 0);
        // model.position.set(0, 0, 0.4);
        model.traverse(function (object) {
          if (object.isMesh) {
            object.castShadow = true; // shadow
            object.receiveShadow = true; // Accept the shadow of others
          }
        });
        defaultQuaternion = model.quaternion.clone();

        scene.add(model);
        renderer.render(scene, camera);

        rotation = true;
        onPreview();
      });
    }
  });
</script>


<div class="h-fit w-fit mx-auto" id="dice-board" />

<footer class="absolute top-[99.6%] inset-x-0 bottom-4 text-center z-40"> 
  <button   
    class="primary-button p-0.5 rounded-2xl"
    disabled={rolling} 
    on:click={onRollDice} 
  >
    <span class="primary-button-inner inline-block font-semibold w-48 py-2.5 rounded-2xl">
      {rolling ? "rolling..." : "ROLL THE DICE"}
    </span>
  </button>
</footer>

<!-- 
  <main class="flex justify-center h-screen bg-slate-900 pb-20">
  <section class="w-fit mx-auto">
    <h1 class="text-xl font-semibold text-center text-white pb-2 pt-10 md:pt-20">
      Dice roller
    </h1>

    <div class="dice-border p-[1px] rounded-md relative">
      {#if preloading}
        <span class="absolute text-white top-[45%] w-full text-center opacity-70 font-medium tracking-widest">
          preloading...
        </span>
      {/if}
      <div class="h-fit w-fit mx-auto rounded-md bg-gray-900" id="dice-board" />
    </div>
  </section> 
</main> 
-->

<style>
.dice-border {
  background: #AA771C;
  background:linear-gradient(to right, #BF953F, #FCF6BA, #B38728, #FBF5B7, #AA771C);
}


.primary-button {
  background: linear-gradient(95.42deg, #FCD161 -15.22%, #E63801 115.22%);
}

.primary-button-inner {
  background: linear-gradient(180deg, #00386C 0%, #121212 100%);
  color: #F0AB00;
}
</style>