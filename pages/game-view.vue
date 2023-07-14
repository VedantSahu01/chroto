
<script setup>
import config from '@/src/config.js';
import { useMouse } from '@vueuse/core';
import { useSound } from '@vueuse/sound';

const { x, y } = useMouse({ touch: false });
const mouseXCordinates = ref(1925);
const displayValue = ref(0);
const {play} = useSound("/sounds/clickSound.wav");
const isSpanHidden = ref(false)

    function playSound(){
      play();
    }

    onMounted( () => {
      document.addEventListener("mousemove", () => {
        isSpanHidden.value = false;
        const oldVal = Math.round(mouseXCordinates.value);
        mouseXCordinates.value = 1920 + ((x.value - window.innerWidth*0.1 )* 100/ (0.8*window.innerWidth));
        if(oldVal!=Math.round(mouseXCordinates.value) && Math.round(mouseXCordinates.value)%5==0){
          console.log(Math.round(mouseXCordinates));
          play();
        }
        displayValue.value = (mouseXCordinates.value>1920 && mouseXCordinates.value <2020)? Math.round(mouseXCordinates.value): (mouseXCordinates.value<1920)?1920:2020;
        if(mouseXCordinates.value>2020 || mouseXCordinates.value<1920){
          isSpanHidden.value = true;
        }
      })
    })


</script>

<template>   
  <div class="game-main-screen">
    <nuxt-img class="image-viewbox" src="/images/test_img_1935.jpg" fit="contain"/>
    <span class="thumb-value" :style="{'left': x + 'px'}" :hidden="isSpanHidden">{{ displayValue }}</span>
    <div class="vertical-club">
      <span v-for="item in 100" class="vertical-line"></span>
    </div>
    <input class="range-selector" type="range" min="1920" max="2020" v-model="mouseXCordinates" step="1"/>
  </div>
</template>

<style>

@font-face {
    font-family: "Orbitron";
    src: url(@/src/assets/fonts/Orbitron-VariableFont_wght.ttf);
  }

  .image-viewbox{
    height: 100%;
    width: 100%;
    object-fit: cover;
  }

  .game-main-screen{
    width: 100%;
    height: 100vh;
    padding: 0px;
    margin: 0px;
    overflow: hidden;
  }
  input[type="range"]{
    -webkit-appearance: none;
    appearance: none;
    background: transparent;
    cursor: pointer;
    position: absolute;
    left: 10vw;
    top: 90vh;
    z-index: 10;
    width: 80vw;
    outline: #000000;
    border-radius: 50%;
  }

  input[type="range"]::-webkit-slider-thumb {
   -webkit-appearance: none; /* Override default look */
   appearance: none;
   margin-top: -10px; /* Centers thumb on the track */
   border: 0.2vw solid white;
   height: 6.1vh;
   width: 1vw;   
   border-radius: 20%; 
   mix-blend-mode: overlay;
  }

  .thumb-value{
    position: absolute;
    background-color: white;
    border: 0.15vw solid black;
    top: 83vh;
    padding: 0.4%;
    z-index: 10;
    border-radius: 20%;
    mix-blend-mode: overlay;
    font-size: 1.3rem;
    font-weight: 900;
    font-family: "Orbitron";
  }

  .vertical-line{
    display: inline-block;
    border: 0.15vw solid white;
    border-top: transparent;
    border-bottom: transparent;
    height: 5vh;
    flex: 1;
    mix-blend-mode: overlay;
  }
  .vertical-club{
    position: absolute;
    left: 10.7vw;
    top: 89.5vh;
    width: 79vw;
    display: flex;
    flex-wrap: wrap;
  }
</style>