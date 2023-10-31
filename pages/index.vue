
<script setup>
  import titleView from "~/views/title-view.vue"; 
  import mainContentView from "~/views/main-content-view.vue"; 
  import footerActionView from "~/views/footer-action-view.vue"; 

  const zoomTransitionFlag = ref(false);
  const wordNormal = ref(["C", "H", "R", "O", "T", "O"]);
  const wordFinal = ref(["C", "H", "R", "O", "T", "O"]);

  function onReceivingTransition(){
    zoomTransitionFlag.value = true;
  }

</script>

<template>
    <title-view :receivedZoomTransition="zoomTransitionFlag" :recievedWordNormal="wordNormal" :recievedWordFinal="wordFinal"></title-view>
    <main-content-view @emmited-zoom-transition="onReceivingTransition()"></main-content-view>
    <footer-action-view :receivedZoomTransition="zoomTransitionFlag"></footer-action-view>
</template>

<style>
  body {
  margin: 0;
}

</style>