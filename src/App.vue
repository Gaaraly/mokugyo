<script setup lang="ts">
import { useSound } from '@vueuse/sound'
import knocked from '/knock.mp3'

const { play } = useSound(knocked)
</script>

<template>
  <main
    font-sans
    p="x-4 y-10" text="center gray-700 dark:gray-200"
    h-screen w-screen
  >
    <div
      w-full h-full
      flex justify-center items-center select-none
      animate-bounce-in animate-duration-none
      active:animate-none hover:animate-duration-500
      @click="play()"
    >
      <!-- Hi -->
      <img
        src="/muyu.png"
        alt="mokugyo" w-auto
        h-auto max-w-full max-h-full cursor-pointer
        filter drop-shadow-xl invert-100
        dark:invert-0
      >
    </div>
    <Footer />
  </main>
</template>
