<script setup>

import {onMounted, ref} from "vue";

onMounted(() => {
  display.value = name
})

const display = ref('')
const name = ref('AaronBarratt')
let timer = null

const randomBit = () => {
  return Math.round(Math.random())
}

const newBinary = () => {
  const len = name.value.length
  let bin = ''
  for (let i = 0; i < len; i++) {
    bin += randomBit()
  }
  return bin
}

const showBinary = () => {
  display.value = newBinary()
  timer = setInterval(() => {
    display.value = newBinary()
  }, 100)
}

const showName = () => {
  clearInterval(timer)
  display.value = name.value
}

</script>

<template>
  <header>
    <div id="header">
      <div id="header-content">
        <p id="title" @mouseover="showBinary" @mouseout="showName">{{ display }}</p>
        <p id="tagline">Python |  JavaScript | Go | SQL</p>
      </div>
    </div>
  </header>

  <main>
  </main>
</template>

<style lang="scss" scoped>

#header {
  margin-top: 1rem;

  #header-content {
    margin: 0 auto;
    width: fit-content;
    align-content: center;
    text-align: center;
  }

  #title {
    font-family: "JetBrains Mono Extra Bold", "Fira Code", monospace;
    font-size: 8rem;
    font-weight: 800;
    margin-top: -2rem;
    cursor: pointer;
    user-select: none;
  }

  #tagline {
    font-family: "JetBrains Mono", "Fira Code", monospace;
    font-size: 1.1rem;
    font-weight: 100;
    margin-top: -1.5rem;
  }
}

</style>
