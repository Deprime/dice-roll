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

    import { onMount } from 'svelte';

    // Data
    let model;
    let mixer;
    let rollAnimation;
    let preloading = true;
    let rolling = false;

    const maxWidth = 700
    const width = (window.innerWidth > maxWidth) 
      ? maxWidth - 8
      : window.innerWidth - 8;
    const height = width; // 400;
    const dimension = 1.1;

    let clock = new Clock();
    const scene = new Scene();
    const camera = new OrthographicCamera(-dimension, dimension, dimension, -dimension, 0.1, 400);

    camera.position.y = 1;
    camera.lookAt(new Vector3(0, 0, 0));

    // Lighting
    // const punctualLights = true;
    const exposure = 0.0;
    const toneMapping = LinearToneMapping;
    const ambientIntensity = 0.5;
    const ambientColor = '#FFFFFF';
    const directIntensity = 0.8 * Math.PI;
    const directColor = '#FFFFFF';

    const renderer = new WebGLRenderer({ antiAlias: true, alpha: true });
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
    light2.position.set(0.5, 1, 0.866); // ~60º
    light2.name = 'main_light';
    camera.add(light2);
    scene.add(light2);

    const loader = new GLTFLoader();

    // Lifecycle
    const prepareAnimation = () => {
      const time = 10;
      rolling = true;
      mixer = new AnimationMixer(model);
      const action = mixer.clipAction(rollAnimation).setDuration(10);
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

    const onRollDice = () => {
      if (rolling) {
        return;
      }
      prepareAnimation();
      render();
    };

    onMount(() => {
      // renderer.render(scene, camera);
      const diceBoard = document.getElementById('dice-board');
      if (diceBoard) {
        diceBoard.appendChild(renderer.domElement);

        //  TODO: define device to choose model size
        loader.load('/glb-models/dice1_512.glb', function (gltf) {
          preloading = false;
          rollAnimation = gltf.animations[0];
          model = gltf.scene;
          model.position.set(0, 0, 0.4);

          model.traverse(function (object) {
            if (object.isMesh) {
              object.castShadow = true; // shadow
              object.receiveShadow = true; // Accept the shadow of others
            }
          });
          scene.add(model);
          renderer.render(scene, camera);
        });
      }
    });
</script>

<main class="  flex items-center justify-center h-screen bg-slate-950 ">
  <section class="w-fit mx-auto">
    <h1 class="text-xl font-semibold text-center text-white pb-2">
      Dice roller
    </h1>

    <div class="dice-border p-0.5 rounded-md ">
      <div class="h-fit w-fit mx-auto rounded-md bg-slate-950" id="dice-board" />
    </div>
  </section>

  <footer class="fixed inset-x-0  bottom-4 text-center"> 
    <button on:click={onRollDice} disabled={rolling} class="px-20 md:px-10 py-2 bg-amber-600 disabled:opacity-50 text-white font-semibold rounded-md">
      {rolling ? "rolling..." : "Roll"}
    </button>
  </footer>
</main>

<style>
  .dice-border {
    background: rgb(253,29,29);
    background: linear-gradient(90deg, rgb(207, 179, 18) 6%, rgba(252,176,69,1) 100%);
  }
</style>