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


  // Grid
  scene.add(new GridHelper(5, 30));

  const loader = new GLTFLoader();
  let rotated = false;

  // Lifecycle
  const render = () => {
    requestAnimationFrame(render);
    if (mixer) {
      const delta = clock.getDelta();

      mixer.update(delta);
      // if (mixer.time >= 4 && !rotated) {
      //   sceneModel.rotateX(5.3)
      //   sceneModel.rotateZ(5.3)
      //   rotated = true;
      // }
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
    prepareAnimation();
    render();
  };

  const prepareAnimation = () => {
    const time =  9.3;
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
      loader.load('/glb-models/dice5.glb', function (gltf) {
        // console.log(gltf);

        preloading    = false;
        rollAnimation = gltf.animations;
        sceneModel    = gltf.scene;

        // const scale = 0.016
        const scale = 1.001
        // sceneModel.children[0].scale.set(scale, scale, scale);
        // rollAnimation.tracks[2].values = rollAnimation.tracks[2].values.map(el => scale);

        sceneModel.position.set(0, 0, 0.6);
        // sceneModel.children[0].rotateX(1);
        // sceneModel.children[0].rotateY(1);

        const relDice = sceneModel.children[0];

        const baseDice = sceneModel.children[1];

        sceneModel.children = [
          baseDice
        ];

        const group = sceneModel.children[0];
        // let rot = 0
        // let rotY = 1.2
        // let rotZ = 0.5
        // group.children[0].rotateX(rot);
        // group.children[0].rotateY(rotY);
        // group.children[0].rotateZ(rotZ);
        // group.children[0].scale.set(2, 2, 2);
        // group.children[1].scale.set(scale, scale, scale);
        // console.log(group.children)
        // sceneModel.children[1].visible = false;
        // sceneModel.traverse(function (object) {
        //   if (object.isMesh) {
        //     object.castShadow = true; // shadow
        //     object.receiveShadow = true; // Accept the shadow of others
        //   }
        // });

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
      {rolling ? "rolling..." : "ROLL THE DICE"}
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
