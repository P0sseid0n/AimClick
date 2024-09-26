<script setup lang="ts">
const props = defineProps<{ posX: number, posY: number, dotClick: () => {} }>()
</script>

<template>
   <div @click="dotClick"></div>
</template>

<style scoped>
div {
   width: 64px;
   height: 64px;
   border-radius: 50%;
   background-color: #C31414;
   position: absolute;
   top: v-bind(posY + "px");
   left: v-bind(posX + "px");
}
</style>