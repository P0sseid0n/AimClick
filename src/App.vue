<script setup lang="ts">
import { reactive, ref } from 'vue';
import DotClicker from './components/DotClicker.vue';

const points = ref(0)

const dots = reactive([
   { posX: 10, posY: 100 },
])

function DotClick(dotIndex: number) {
   points.value += 1;
   dots.splice(dotIndex, 1)
   if (dots.length == 0) addDot()
}

function addDot() {
   dots.push({
      posX: Math.floor(Math.random() * (window.innerWidth - 64)),
      posY: Math.floor(Math.random() * (window.innerHeight - 64))
   })
}

addDot()

setInterval(() => {
   if (dots.length < 10) addDot()
}, 1000)

</script>

<template>
   <main>
      <h1>{{ points }}</h1>

      <DotClicker v-for="(dot, index) in dots" v-bind="dot" :dotClick="() => DotClick(index)" />
   </main>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Teko:wght@700&display=swap');

* {
   margin: 0;
   padding: 0;
   box-sizing: border-box;
}

h1 {
   font-size: 80px;
   text-align: center;
   color: #C31414;
   position: absolute;
   left: 50%;
   transform: translateX(-50%);
   top: 16px;
   font-family: 'Teko', sans-serif;
}

#app {
   width: 100vw;
   height: 100vh;
}

main {
   background: rgb(24, 24, 24);
   width: 100%;
   height: 100%;
}
</style>
