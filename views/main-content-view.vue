
<script setup>
import config from '@/src/config.js';
const zoomTransitionFlag = ref(false);
const emitZoomTransition= defineEmits(["emmitedZoomTransition"])


function performStartTransition() {
  emitZoomTransition("emmitedZoomTransition", true);
  zoomTransitionFlag.value = true;
}

</script>

<template>
  <div :class="{'rounded-box': true, 'zoom-animation': zoomTransitionFlag}" @click="performStartTransition()">
    <NuxtLink to="/game-view" class="link-area">
    </NuxtLink>
  </div>
</template>

<style>
  .rounded-box{
    width: 75%;
    height: 500px;
    border-style: solid;
    border-color: black;
    border-width: 5px;
    border-radius: 25px;
    padding: 15px;
    margin: 15px 11%;
  }
  .zoom-animation{
    height: 720px;
    width: 95%;
    margin: 5px 1%;
    transition: height 0.25s ease-in, width 0.25s ease-in, margin 0.25s ease-in;
  }
  .link-area{
    display: block;
    width: 100%;
    height: 100%;
  }
</style>