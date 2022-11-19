<script setup lang="ts">
import { useSound } from '@vueuse/sound'
import type { VNode } from 'vue'
import knocked from '/knock.mp3'

interface ITip {
  id: string
  component: VNode
  show: boolean
}

const lists = $ref<ITip[]>([])
const { play } = useSound(knocked)

const listsExposed = computed(() => lists.filter(it => it.show))

const theTip = h('span', {
  class: 'absolute right-20 top-10 text-xl ease-out duration-800 tips',
}, 'Click me')

// const { proxy } = getCurrentInstance() as any

const onClick = () => {
  play()
  const id = `${Date.now()}id`
  lists.push({ component: theTip, id, show: true })
  // console.log(listsRef.value.map(it=>it.key))
  setTimeout(() => {
    // proxy.$refs[id][0].remove()
    lists.at(-1)!.show = false
  }, 900)
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
        <!-- <component :is="tip.component" v-for="tip in lists" :key="tip.id" :ref="tip.id" /> -->
        <component :is="tip.component" v-for="tip in listsExposed" :key="tip.id" />
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

.tips {
  animation: fadeOutUp 1s ease-in-out;
}
</style>
