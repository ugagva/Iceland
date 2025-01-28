<script setup lang="ts">


import {onMounted, ref} from "vue";

const wrapper=ref<null | HTMLElement>(null)
const options={
  threshold: 0.5,
}

onMounted(()=> {
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            wrapper.value?.classList.add("animated");
            setTimeout(()=>{
              wrapper.value?.classList.add("hoverAdded");
            },2000)
          }else {
            wrapper.value?.classList.remove("animated");
            wrapper.value?.classList.remove("hoverAdded");
          }
        })
      },options);
      if (wrapper.value) {observer.observe(wrapper.value)}
      ;
    }
)

</script>

<template>
<div class="root">
  <div ref="wrapper" class="h2 ">
    Believe
    <span class="believe first"> Believe </span>
    <span class="believe second">Believe </span>
    <span class="believe third">in yourself </span>
  </div>
</div>
</template>

<style scoped lang="sass">
@import "../assets/styles/main"

@keyframes pushTopEffect
  0%, 100%
    top: 0
  50%
    top: -18px

@keyframes pushBottomEffect
  0%, 100%
    top: 0
  50%
    top: 18px

@keyframes showEffect
  0%, 100%
    transform: translateY(-50%) scaleY(0)
  50%
    transform: translateY(-50%) scaleY(1)


.root
  position: relative
  height: 100vh
  font-family: monospace


.h2
  position: absolute
  top: 50%
  left: 50%
  font-size: 6em
  font-weight: 700
  color: transparent
  text-transform: uppercase
  transform: translate(-50%, -50%)


.believe
  position: absolute
  top: 0
  left: 0
  color: $black
  transition: 0.5s
  overflow: hidden

  &.first
    clip-path: polygon(0 0, 100% 0, 100% 50%, 0 50%)
  &.second
    clip-path: polygon(0 50%, 100% 50%, 100% 100%, 0 100%)


.third
  position: absolute
  top: 50%
  left: 0
  margin-left: 5px
  width: calc(100%  - 10px)
  padding-left: 20px
  font-size: 0.25em
  font-weight: 500
  letter-spacing: 0.7em
  text-align: center
  color: #000000
  background-color: #ff0
  transition: .5s
  transform: translateY(-50%) scaleY(0)

.h2.hoverAdded:hover
  .first
    transform: translateY(-18px)
  .second
    transform: translateY(18px)
  .third
    transform: translateY(-50%) scaleY(1)


.h2.animated
  .first
    animation: pushTopEffect 1s ease 0.5s 1
  .second
    animation: pushBottomEffect 1s ease 0.5s 1
  .third
    animation: showEffect 1s ease 0.5s 1




</style>