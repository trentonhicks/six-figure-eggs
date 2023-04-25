<script setup>
import { onMounted, defineEmits } from 'vue';
import chicken from '../assets/chicken-in-egg-sprite.svg'

const emit = defineEmits(['animation-ended'])

onMounted(() => setTimeout(() => emit('animation-ended'), 2000))
</script>

<template>
  <div class="h-screen flex items-center fixed inset-0">
      <div class="w-full move-right-to-left translate-x-full">
        <div class="h-80 w-80">
          <div :style="`background-image: url(${chicken})`" class="chicken chicken-running" />
        </div>
      </div>
  </div>
</template>

<style>
  .chicken {
    height: 100%;
    width: 100%;
    background-size: 239%;
    background-position: 0 0;
    background-repeat: no-repeat;
  }

  .chicken-running {
    animation-name: chicken-running-animation;
    animation-duration: 0.7s;
    animation-iteration-count: infinite;
    animation-timing-function: steps(1);
    animation-fill-mode: forwards;
  }

  .move-right-to-left {
    animation-name: move-right-to-left-animation;
    animation-duration: 4s;
    animation-timing-function: ease;
    animation-fill-mode: forwards;
  }

  @keyframes chicken-running-animation {
    0% {
      background-position: 0 0;
      clip-path: inset(0);
    }
    16.6666666667% {
      background-position: 72% 0;
      clip-path: inset(0 19.5% 0 0);
    }
    33.3333333334% {
      background-position: 129.9% 0;
      clip-path: inset(0);
    }
    50.0000000001% {
      background-position: 0 101%;
      clip-path: inset(0);
    }
    66.6666666668% {
      background-position: 75.7% 101%;
      clip-path: inset(0 30% 0 0);
    }
    83.3333333335% {
      background-position: 129.7% 101%;
      inset: 0;
    }
    100% {
      background-position: 0 0;
      clip-path: inset(0);
    }
  }

  @keyframes move-right-to-left-animation {
    from {
      transform: translateX(100%);
    }
    to {
      transform: translateX(-100%);
    }
  }

</style>