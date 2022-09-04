<script setup>
import { ref } from "vue"
import Cursor1 from "./components/cursor1.vue"

const isPlaying = ref(false)
const delay = ref(null)

const start = () => {
  isPlaying.value = true
  delay.value = 2000
}
</script>

<template>
  <h1 class="ninja">Ninja Reaction Timer🥷</h1>
  <button @click="start">
    <span class="text">play</span>
    <span class="perk">🌀</span>
  </button>
  <div class="cursor-container">
    <Cursor1 />
  </div>
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
