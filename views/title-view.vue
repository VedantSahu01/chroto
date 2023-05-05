
<script setup>
import config from '@/src/config.js';

defineProps(['receivedZoomTransition']);

const wordFinal = ref(["C", "H", "R", "O", "T", "O"])
const wordNormal = ref(["C", "H", "R", "O", "T", "O"])
const wordFlipped = ref(["𑀲𑀻", "𑀏𑀘", "𑀆𑀭", "𑀑", "𑀝𑀻", "𑀑"])
const randomNum = ref(0)
const animated = ref([false, false, false, false, false, false]);
// setTimeout works asynchronously!!
function createTitle() {
  randomNum.value = Math.round(Math.random() * 5);
  wordFinal.value[randomNum.value] = wordFlipped.value[randomNum.value];
  flipAnimation(randomNum);
  setTimeout(() => { 
    resetValue(wordFinal, randomNum, wordNormal);
  }, config.MainTitle.FLIPPED_TIME);
}

function flipAnimation(randomNum){
  animated.value[randomNum.value] = !animated.value[randomNum.value];
  setTimeout(() => {
    animated.value[randomNum.value] = !animated.value[randomNum.value]
  }, config.MainTitle.FLIP_ANIMATION_TIME)
}


function resetValue(wordFinal, randomNum, wordNormal) {
  flipAnimation(randomNum);
  wordFinal.value[randomNum.value] = wordNormal.value[randomNum.value];
}

onMounted( () => {
  window.setInterval(() => {
    createTitle();
  }, config.MainTitle.FLIP_INTERVAL);
}
)  
</script>

<template>
  <div :class="{'title_div': true, 'remove-div-animation': receivedZoomTransition}">
    <span v-for="(element, index) in wordFinal" :class="{'title_letter': true, 'flip_animation': animated[index]}">{{ element }}</span>
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
  .title_div{
    text-align: center;
    font-family: "Orbitron", "NotoSansBrahmi";
    font-size: 40px;
    font-weight: 600;
    letter-spacing: 10px;
    height: 100px;
  }
  .title_letter{
    padding-left: 50px;
    padding-right: 50px;
    display: inline-block;
    width: 50px;
    line-height: 100px;
    /* animation: flip 0.2s ease-in-out ; */
  }
  .flip_animation{
    animation: flip 0.2s ease-in-out ;
  }
  .remove-div-animation{
    opacity: 0;
    height: 0px;
    transition: height 0.25s ease-in, opacity 0.15s ease-out;
  }
</style>