<script setup>
import { ref } from "vue"
import Cursor1 from "./components/cursor1.vue"
import Block from "./components/Block.vue"

const isPlaying = ref(false)
const delay = ref(null)

const start = () => {
  isPlaying.value = true
  delay.value = Math.floor(2000 + Math.random() * 5000)
}
</script>

<template>
  <h1 class="ninja">Ninja Reaction 🥷</h1>
  <button @click="start" :disabled="isPlaying">
    <span class="text">play</span>
    <span class="perk">🌀</span>
  </button>
  <div class="cursor-container">
    <Cursor1 />
  </div>
  <Block v-if="isPlaying" :delay="delay" />
</template>

<style scoped>
.ninja {
  /* height: 6em;
  padding: 1.5em; */
  will-change: filter;
}
.ninja:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
