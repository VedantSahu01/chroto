
<script setup>
  import titleView from "~/views/title-view.vue"; 
  import mainContentView from "~/views/main-content-view.vue"; 
  import footerActionView from "~/views/footer-action-view.vue"; 

  const zoomTransitionFlag = ref(false);

  function onReceivingTransition(){
    zoomTransitionFlag.value = true;
  }

</script>

<template>
    <title-view :receivedZoomTransition="zoomTransitionFlag"></title-view>
    <main-content-view @emmited-zoom-transition="onReceivingTransition()"></main-content-view>
    <footer-action-view :receivedZoomTransition="zoomTransitionFlag"></footer-action-view>
</template>

<style>
  body {
  margin: 0;
}

</style>