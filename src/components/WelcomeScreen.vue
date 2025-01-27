<script setup lang="ts">
import {onMounted, onUnmounted, ref} from 'vue';

const layer = ref<null | HTMLElement>(null)





const movePlane=()=>{
  const scrollY=window.scrollY

      if (layer.value){
          layer.value.style.left =`${scrollY}px`
      }
}

onMounted(()=>{
  window.addEventListener('scroll',movePlane)
})


onUnmounted(()=>{
  window.removeEventListener('scroll',movePlane)
})
</script>




<template>
  <div class="root">
  <div ref="layer" class="layer">

    <div class="texts">
      <div class="title">
        Начните путешествие в
        <div class="content">
          <span class="accent accent-stoke"> Исландию</span><br/>
          <span class="accent accent-wave"> Исландию</span><br/>

        </div>
        прямо сейчас
      </div>
    </div>
    <img src="../icons/plane.png" alt="Plane" class="plane">
  </div>
    <div class="bg bg-1"></div>
    <div class="welcome-block">
      <div class="welcome-text">
        Welcome to
        <div class="transparent-text"> Iceland</div>
      </div>
    </div>
    <div class="bg bg-2"></div>



  </div>
</template>



<style lang="sass"  scoped >
@import '../assets/styles/main'
@keyframes wave
   0%, 100%
     clip-path: polygon(0% 39%, 9% 41%, 18% 45%, 24% 50%, 31% 55%, 39% 60%, 46% 62%, 53% 62%, 62% 59%, 68% 54%, 76% 50%, 83% 49%, 90% 50%, 97% 52%, 100% 54%, 100% 100%, 0% 100%)
   50%
     clip-path: polygon(0 49%, 5% 53%, 11% 57%, 16% 59%, 28% 64%, 38% 57%, 41% 58%, 48% 56%, 54% 58%, 64% 62%, 71% 66%, 79% 68%, 86% 66%, 92% 64%, 100% 62%, 100% 100%, 0% 100%)

.root
   font-family: "Poppins", sans-serif
   color: $white
   background-color: $backgroundColor

.layer
  position: fixed
  left: 0
  height: 100vh
  width: 100%
  background-color: $backgroundColor


.texts
  position: absolute
  left: 50%
  top: 50%
  text-align: center
  font-family: "Roboto", "Arial", sans-serif
  font-size: 44px
  font-weight: 700
  letter-spacing: .05em
  transform: translate(-50%, -50%)


.plane
  z-index: 2
  position: absolute
  left: -50vh
  height: 100vh


.bg
  background-size: cover
  background-attachment: fixed

.bg-1
  background-image: url("../icons/bg1.jpg")
  height: 240vh


.welcome-block
  height: 50vh
  display: flex
  justify-content: center
  align-items: center
  text-align: center

.welcome-text
  font-size: 3em
  font-weight: 200
  letter-spacing: .25em
  line-height: 2.5em
  color: #ffffff
  text-transform: uppercase


.transparent-text
  font-size: 4em
  font-weight: 900
  letter-spacing: 0
  background-size: cover
  background: url("../icons/bg2.jpeg") fixed
  -webkit-background-clip: text
  background-clip: text
  color: transparent



.bg-2
  background-image: url("../icons/bg2.jpeg")
  height: 130vh

.content
  position: relative
.accent
  position: absolute
  left: 50%
  top: 50%
  font-size: 120px
  color: transparent
  transform: translate(-50%, -50%)


.accent-stoke
  -webkit-text-stroke: 2px $accentColor


.accent-wave
  color: $accentColor
  animation: wave 4s ease-in-out infinite


</style>