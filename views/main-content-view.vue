
<script setup>
import config from '@/src/config.js';
const zoomTransitionFlag = ref(false);
const emitZoomTransition = defineEmits(["emmitedZoomTransition"])


function performStartTransition() {
  emitZoomTransition("emmitedZoomTransition", true);
  zoomTransitionFlag.value = true;
}

</script>

<template>
  <div :class="{ 'camera-lens': true, 'zoom-animation': zoomTransitionFlag }" @click="performStartTransition()">
    <NuxtLink to="/game-view" class="link-area">
      </NuxtLink>
  </div>
</template>

<style>
body {
  background-color: #050505; /* Adjust this to a darker color */
  margin: 0;
}
.camera-lens {
  width: 75vw;
  height: 55vh;
  border: double 4vw transparent;
  background-image: linear-gradient(#999993, #999993),linear-gradient(to bottom, #080A09, #323E3D); /* Adjust the color for a metallic look */
  background-origin: border-box;
  background-clip: padding-box, border-box;
  box-shadow: 
    2vw 3vh 0 #141a17,
    inset 2vw 3vh 0 #293332;
  border-radius: 100px;
  padding: 15px;
  /* background: white;Metallic gradient background */
  margin: 0.5vh auto 3.5vh auto;
  display: flex;
  justify-content: center;
  align-items: center;
}

.zoom-animation {
  height: 720px;
  width: 95%;
  margin: 5px 1%;
  transition: height 0.25s ease-in, width 0.25s ease-in, margin 0.25s ease-in;
}

.link-area {
  display: block;
  width: 100%;
  height: 100%;
  border-radius: 3vw;
  overflow: hidden;
}
</style>