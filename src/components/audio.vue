<template>
  <div class="audio-container" @click="playAudio">
    <div class="audio-play" v-if="audio">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
        class="feather feather-volume-2"
      >
        <polygon points="11 5 6 9 2 9 2 15 6 15 11 19 11 5"></polygon>
        <path
          d="M19.07 4.93a10 10 0 0 1 0 14.14M15.54 8.46a5 5 0 0 1 0 7.07"
        ></path>
      </svg>
    </div>
    <div v-else class="audio-pause">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
        class="feather feather-volume-x"
      >
        <polygon points="11 5 6 9 2 9 2 15 6 15 11 19 11 5"></polygon>
        <line x1="23" y1="9" x2="17" y2="15"></line>
        <line x1="17" y1="9" x2="23" y2="15"></line>
      </svg>
    </div>
    <!--

      Get a speaker icon and set that up to play Ninja sounds
    -->
  </div>
</template>

<script setup>
import { ref } from "vue"
import { useSound } from "@vueuse/sound"
import buttonSfx from "../assets/audio/click2.mp3"

const audio = ref(false)
const { play } = useSound(buttonSfx)

const emit = defineEmits(["playAudio"])

function playAudio() {
  audio.value = !audio.value
  play()
  emit("playAudio", audio.value)
}
</script>

<style>
.audio-container {
  position: absolute;
  top: 20px;
  right: 20px;
  color: #fff;
  border: 1px solid #0faf87;
  padding: 0.3em;
  padding-bottom: 0.1em;
  box-shadow: 3px 15px 8px -10px rgba(0, 0, 0, 0.3);
  /* border-top-left-radius: 37px 140px;
  border-top-right-radius: 23px 130px;
  border-bottom-left-radius: 110px 19px;
  border-bottom-right-radius: 120px 24px; */
  transform: rotate(-3deg);
}

.audio-container:active {
  transform: rotate(0deg);
}
</style>
