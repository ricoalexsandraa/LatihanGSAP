<script setup>
import { onMounted, ref } from 'vue';

const main = ref();
let ctx;
let tl;

function toogleTimeline(){
  tl.reversed(!tl.reversed())
}

onMounted(() => {
  ctx = gsap.context(() => {
    tl = gsap.timeline({ defaults: { duration: 0.5 }})
    .to('.box1', { x: '400px' })
    .to('.box2', { x: '-200px' })
    .to('.box3', { x: '100px' })
    .reverse()
  })

  return toogleTimeline

}, main.value);

</script>

<template>
  <div class="p-2 m-2 justify-center grid gap-2">
    <div class="text-xl text-slate-900 font-bold text-center"> Use the button to toggle a Timeline </div>
    <button class="m-3 p-3 bg-green-500 rounded-md font-medium hover:bg-green-600 hover:text-white" @click="toogleTimeline"> TOOGLE TIMELINE </button>
    <div class="box1 p-5 w-15 bg-green-500 text-white font-medium rounded-md text-center justify-self-center"> Box 1 </div>
    <div class="box2 p-5 w-15 bg-green-500 text-white font-medium rounded-md text-center justify-self-center"> Box 2 </div>
    <div class="box3 p-5 w-15 bg-green-500 text-white font-medium rounded-md text-center justify-self-center"> Box 3 </div>
  </div>
</template>

