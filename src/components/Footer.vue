<template>
  <nav text-xl mt-2 inline-flex gap-2>
    <button icon-btn @click="toggleDark()">
      <div dark:i-carbon-moon i-carbon-sun />
    </button>

    <a
      icon-btn i-carbon-logo-github
      rel="noreferrer"
      href="https://github.com/gaaraly/mokugyo"
      target="_blank"
      title="GitHub"
    />
  </nav>
</template>
