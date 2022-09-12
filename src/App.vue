<script setup>
import { ref } from "vue"
import Cursor1 from "./components/cursor1.vue"
import Block from "./components/Block.vue"

const isPlaying = ref(false)
const delay = ref(null)
const score = ref(null)

const start = () => {
  isPlaying.value = true
  delay.value = Math.floor(2000 + Math.random() * 5000)
}

const endGame = (reactionTime) => {
  score.value = reactionTime
  isPlaying.value = false
}

//always remember that the custom event you emit, takes the second parameter as an argument
//and you can extract it from a function.
</script>

<template>
  <h1 class="ninja">Ninja React🥷</h1>
  <button @click="start" :disabled="isPlaying">
    <span class="text">play</span>
    <span class="perk">🌀</span>
  </button>
  <div class="cursor-container">
    <Cursor1 />
  </div>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <p>
    Reaction time: <span class="score">{{ score }}</span
    >ms
  </p>
</template>

<style>
#app {
  max-width: 1024px;
  overflow: hidden;
}

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

.score {
  font-family: "Assassin Ninja";
  font-family: "Asian Ninja";
}
</style>
