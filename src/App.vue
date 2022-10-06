<script setup lang="ts">
function handleCilck() {
  // eslint-disable-next-line no-console
  console.log('click')
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
      @click="handleCilck"
    >
      <!-- Hi -->
      <img
        src="/muyu.png" alt="mokugyo"
        w-auto h-auto max-w-full max-h-full
        cursor-pointer
        animate-bounce-in animate-duration-none
        active:animate-none hover:animate-duration-500
      >
    </div>
    <Footer />
  </main>
</template>
