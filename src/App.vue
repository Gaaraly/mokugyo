<script setup lang="ts">
import { useSound } from '@vueuse/sound'
import knocked from '/knock.mp3'

const timeStamp = $ref(new Date())
const { play } = useSound(knocked)
const tipRef = $ref<HTMLSpanElement>()

let count = $ref(1)
const theTip = h('span', {
  class: 'absolute right-20 top-10 text-xl ease-out duration-800',
}, 'Click me')
const lists = $ref<ITip[]>([])

const onClick = () => {
  play()
  lists.push({ theTip, which: toRaw(++count) })
  // tipRef.style.top = '0'
  tipRef.style.opacity = '100'
  tipRef.style.transform = 'translate3d(0, 0, 0)'
  tipRef.classList.add('transition-all')
  tipRef.style.transform = 'translate3d(0, -100%, 0)'
  tipRef.style.opacity = '0'
}
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
    >
      <div
        relative
        w-auto h-auto max-w-full max-h-full
      >
        <!-- <Tip /> -->
        <component :is="tip.theTip" v-for="tip in lists" :key="tip.which" />
        <!-- <component :is="theTip" ref="tipRef" :key="timeStamp" /> -->
        <img
          src="/muyu.png" class="muyu"
          alt="mokugyo" cursor-pointer
          w-auto h-auto max-w-full max-h-full
          filter drop-shadow-xl dark:invert-0 invert-100
          animate-bounce-in animate-duration-none
          active:animate-none hover:animate-duration-500
          @click="onClick"
        >
      </div>
    </div>
    <Footer />
  </main>
</template>

<style>
@keyframes fadeOutUp {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
    transform: translate3d(0, -100%, 0);
    display: none;
  }
}

/* .tips {
  animation: fadeOutUp 1s ease-in-out;
} */
</style>
