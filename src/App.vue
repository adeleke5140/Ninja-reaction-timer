<script setup>
import { ref, onMounted } from "vue"
import Cursor1 from "./components/cursor1.vue"
import Block from "./components/Block.vue"
import Audio from "./components/audio.vue"

import { useSound } from "@vueuse/sound"
import bgMusic from "./assets/audio/bgmusic.mp3"
import Instructions from "./components/Instructions.vue"
import Results from "./components/Results.vue"

const { play, stop } = useSound(bgMusic, {
  loop: true,
  volume: 0.25
})
const isPlaying = ref(false)
const delay = ref(null)
const score = ref(null)
const showResults = ref(false)

//show shuriken when before

const start = () => {
  isPlaying.value = true
  if (showResults.value) {
    showResults.value = false
  }
  delay.value = generateRandomNumber(2000, 7000)
}

const endGame = async (reactionTime) => {
  score.value = reactionTime
  isPlaying.value = false
  showResults.value = true

  // await new Promise((res) => setTimeout(res, 3000))

  // showResults.value = false
}

const generateRandomNumber = (min, max) => {
  return Math.floor(Math.random() * (max - min + 1)) + min
}

function playNinjaIntro(audio) {
  if (audio === true) {
    play()
  } else {
    stop()
  }
}

onMounted(async () => {
  playNinjaIntro()
})

//always remember that the custom event you emit, takes the second parameter as an argument
//and you can extract it from a function.
</script>

<template>
  <Instructions />
  <Audio @playAudio="playNinjaIntro" />
  <h1 class="ninja">Ninja React🥷</h1>
  <button @click="start" :disabled="isPlaying">
    <span class="text">play</span>
    <span class="perk">🌀</span>
  </button>
  <div class="cursor-container">
    <Cursor1 />
  </div>
  <Block
    v-if="isPlaying"
    :delay="delay"
    @end="endGame"
    :playAudio="playAudio"
  />
  <Results v-if="showResults" :score="score" />
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
</style>
