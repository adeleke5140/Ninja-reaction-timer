<template>
  <div
    v-if="showBlock"
    class="block"
    @click="stopTimer"
    @mousemove="handleKunaiPosition"
    ref="block"
  >
    strike
    <img src="../assets/kunai2.png" class="kunai" ref="kunai" />
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, watchEffect } from "vue"
//current Task
//show shuriken before component shows
//once the components mount but before it shows up

const props = defineProps({
  delay: Number
})

const emit = defineEmits(["end"])

const block = ref(null)

const kunai = ref(null)
const x = ref(0)
const y = ref(0)
const showBlock = ref(false)

const timer = ref(null)
const reactionTime = ref(0)

const blockPositionX = ref(null)
const blockPositionY = ref(null)

const getRandomPosition = (min, max) =>
  Math.floor(Math.random() * (max - min + 1) + min)

function moveBlockRandomly(block) {
  blockPositionX.value = getRandomPosition(300, 700)
  blockPositionY.value = getRandomPosition(300, 700)

  block.style.position = "absolute"
  block.style.top = blockPositionY.value + "px"
  block.style.left = blockPositionX.value + "px"
}

function handleKunaiPosition(e) {
  x.value = e.offsetX
  y.value = e.offsetY

  kunai.value.style.top = y.value + "px"
  kunai.value.style.left = x.value + "px"
}

function toggleShowBlock(props) {
  const { delay } = props
  return setTimeout(() => {
    showBlock.value = true
    watchEffect(() => {
      if (block.value) {
        moveBlockRandomly(block.value)
      }
    })
    startTimer()
  }, delay)
}

function startTimer() {
  timer.value = setInterval(() => {
    reactionTime.value += 10
  }, 10)
}

function stopTimer() {
  clearInterval(timer.value)
  console.log(reactionTime.value)
  emit("end", reactionTime.value)
}

onMounted(() => {
  console.log("component mounted")
  toggleShowBlock(props)
})

onUnmounted(() => {
  console.log("component unmounted")
})

// onUpdated(() => {
//   console.log("component updated")
// })
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  cursor: pointer;
  padding: 100px 0;
  margin: 40px auto;
  cursor: none;
  position: relative;
  transform: rotate(-1deg);
  border-top-left-radius: 37px 140px;
  border-top-right-radius: 23px 130px;
  border-bottom-left-radius: 110px 19px;
  border-bottom-right-radius: 120px 24px;
  border: solid 1px #0faf87;
  transform: rotate(-1deg);
  box-shadow: 3px 15px 8px -10px rgba(0, 0, 0, 0.3);
  transition: all 0.13s ease-in;
  font-weight: bold;
  text-transform: uppercase;
}

.kunai {
  position: absolute;
  width: 15px;
  height: 15px;
  cursor: pointer;
  pointer-events: none;
  transform: rotate(635deg);
}
</style>
