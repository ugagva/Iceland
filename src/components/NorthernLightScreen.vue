<script setup lang="ts">
import {onMounted, ref} from "vue";
import hoverEffect from 'hover-effect'

const distortion = ref<HTMLElement|null>('null');


onMounted(()=>{
          new hoverEffect({
            parent: distortion.value,
            intensity: 0.1,
            image1: "./src/icons/1.jpg",
            image2: './src/icons/2.jpg',
            displacementImage: './src/icons/heightMap.png',
  });
})

</script>

<template>

<div ref="distortion" class="distortion"></div>

</template>

<style scoped lang="sass">
@import "../assets/styles/main"

.distortion
  height: 100vh


</style>