
<script setup>
import config from '@/src/config.js';


defineProps(['receivedZoomTransition']);


</script>

<template>
  <div :class="{'footer_div': true, 'remove-div-animation': receivedZoomTransition}">
    <button class="custom-button">?</button>
  </div>
</template>

<style>
  @font-face {
    font-family: "NotoSansBrahmi";
    src: url(@/src/assets/fonts/NotoSansBrahmi-Regular.ttf);
  }
  @font-face {
    font-family: "Orbitron";
    src: url(@/src/assets/fonts/Orbitron-VariableFont_wght.ttf);
  }
  @keyframes flip {
    0% {transform: rotateX(0);}
    50% {transform: rotateX(90deg);}
    100% {transform: rotateX(0);}
  }
  .remove-div-animation{
    opacity: 0;
    height: 0px;
    transition: height 0.25s ease-in, opacity 0.15s ease-out;
  }
  .custom-button{
      margin-left: 47%;
      padding: 0.8%;
      border-radius: 15%;
      border: 4px solid black;
      font-family: Orbitron;
      font-weight: 800;
      font-size: large;
  }
</style>