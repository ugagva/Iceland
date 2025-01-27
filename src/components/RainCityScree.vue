<script setup lang="ts">

</script>

<template>
<div class="root">
  <div class="section">
    <div class="rain"></div>
  </div>
</div>
</template>

<style scoped lang="sass">
@import "../assets/styles/main"

@keyframes neon
  0%, 100%
      filter: hue-rotate(0)
  50%
    filter: hue-rotate(360deg)

@keyframes rain
  0%
    background-position: 0 0
  100%
    background-position: 2% 100%

@keyframes rainOpacity
  0%, 100%
    opacity: 0.5
  50%
    opacity: 1



.root
  position: relative
  height: 100vh
  background-image: url("../icons/city.jpg")
  background-position: 50% 75%
  animation: neon 3s linear infinite

.rain
  position: absolute
  top: 0
  left: 0
  width: 100%
  height: 100%
  background-image: url("../icons/rain.png")
  animation: rain .2s linear infinite, rainOpacity 10s linear infinite


</style>