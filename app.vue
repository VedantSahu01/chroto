
<script setup>
  import titleView from "./views/title-view.vue"; 
  import mainContentView from "./views/main-content-view.vue"; 

  const zoomTransitionFlag = ref(false);

  function onReceivingTransition(){
    zoomTransitionFlag.value = true;
  }

</script>

<template>
    <title-view :receivedZoomTransition="zoomTransitionFlag"></title-view>
    <main-content-view @emmited-zoom-transition="onReceivingTransition()"></main-content-view>
</template>

<style>
  
</style>