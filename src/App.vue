<script setup>
import { ref } from 'vue';
import { gsap } from 'gsap';

import Logo from './components/Logo.vue';
import LoadingScreen from './components/LoadingScreen.vue';
import EggMan from './components/EggMan.vue';
import bacon from './assets/bacon.webp';
import eggsBackground from './assets/eggs-background.svg';

const showLoadingScreen = ref(true);

function animateCta(element, done) {
  gsap.fromTo(element, { y: 80, opacity: 0, }, { y: 0, opacity: 1, duration: 0.3, delay: 0.5, onComplete: done, })
}
</script>

<template>
    <div>
      <section
        class="h-screen flex flex-col items-center justify-center px-5">
        <div :class="['transition-opacity duration-1000 ease-in-out inset-0 object-cover w-screen h-screen fixed z-0 before:absolute before:inset-0 before:h-screen before:w-screen before:from-white before:from-20% before:to-white/50 before:bg-gradient-to-t', showLoadingScreen ? 'opacity-0' : 'opacity-1']">
            <img
              :src="bacon"
              alt=""
              class="object-cover object-center w-full h-full transition-opacity duration-500"
            />
        </div>

        <template v-if="showLoadingScreen">
          <LoadingScreen
            class="absolute z-10"
            @animation-ended="showLoadingScreen = false"
          />
        </template>

        <template v-else>
          <div class="w-full max-w-xl relative z-10 mb-5">
            <Logo />
          </div>

          <div class="z-10">
            <transition @enter="animateCta" appear>
              <button class="px-7 py-2 text-xl text-white font-bold bg-gradient-to-t from-sky-500 to-sky-300 rounded-md">Go To Instructions</button>
            </transition>
          </div>
        </template>

      </section>

      <main class="relative z-10">
        <section class="text-white px-5 py-20 lg:px-20 lg:py-20 lg:pb-28 bg-gradient-to-t from-sky-500 to-sky-300 flex flex-col justify-center">
          <div>
            <div class="max-w-[250px] mx-auto relative mb-5 lg:mb-7">
              <EggMan />
            </div>
            <div class="max-w-4xl mx-auto">
              <div class="mb-10 lg:mb-14 text-center">
                <h2 class="text-4xl lg:text-5xl uppercase font-bold mb-5">Instructions</h2>
                <p class="text-lg">Looking for a quick and easy breakfast that will fuel your entrepreneurial spirit? Look no further than the perfect fried egg, cooked to perfection in under 30 seconds.</p>
              </div>
              <ol class="text-center grid lg:grid-cols-3 gap-5 lg:gap-7 place-items-center">
                <li class="flex flex-col gap-3">
                  <div class="text-3xl font-bold w-12 h-12 rounded-full bg-gradient-to-t from-sky-950 to-sky-800 flex items-center justify-center text-white mx-auto">1</div>
                  <div class="text-lg">Get a non-stick pan and melt butter over medium-high heat.</div>
                </li>
                <li class="flex flex-col gap-3">
                  <div class="text-3xl font-bold w-12 h-12 rounded-full bg-gradient-to-t from-sky-950 to-sky-800 flex items-center justify-center text-white mx-auto">2</div>
                  <div class="text-lg">Crack an egg into the pan and season it with salt and pepper.</div>
                </li>
                <li class="flex flex-col gap-3">
                  <div class="text-3xl font-bold w-12 h-12 rounded-full bg-gradient-to-t from-sky-950 to-sky-800 flex items-center justify-center text-white mx-auto">3</div>
                  <div class="text-lg">While the egg cooks, turn your passion into a business.</div>
                </li>
              </ol>
            </div>
          </div>
        </section>
        <section class="p-10 lg:py-20 lg:px-20 relative z-20 flex flex-col justify-center">
          <div>
            <div class="relative z-20 grid lg:grid-cols-2 gap-5 max-w-5xl mx-auto place-items-center">
              <img src="./assets/profile.png" class="lg:scale-[1.7] lg:origin-bottom relative lg:top-28 max-w-sm rounded-b-full w-80 h-80 object-contain object-bottom place-self-center lg:place-self-start" />
              <div class="place-self-start flex flex-col gap-5">
                <div class="text-xl lg:text-2xl text-white font-bold text-center lg:text-left">"Thank you from the bottom of my heart for your generous donations. Your support means the world to me as I work towards achieving my entrepreneurial dreams, and it also means I can enjoy a delicious breakfast while I work! Food has always been a source of inspiration and comfort for me, and with your help, I'm one step closer to building a successful online business and sharing my passions with the world."</div>
                <button class="px-7 py-2 text-xl text-white font-bold bg-gradient-to-t from-sky-500 to-sky-300 rounded-md">Donate Now</button>
                <div class="text-xs text-gray-400 text-center"><strong>DISCALIMER:</strong> I'm not actually receiving donations. This is a joke.</div>
              </div>
            </div>
          </div>
          <div class="absolute z-0 h-full w-full bg-cover inset-0" :style="`background-image: url(${eggsBackground})`"></div>
          <div class="absolute z-10 h-full w-full inset-0 bg-sky-950/80"></div>
        </section>
      </main>
    </div>
</template>