<template>
  <div
    v-if="showBlock"
    class="block"
    @click="getDelayAfterClick"
    @mousemove="handleKunaiPosition"
  >
    Click me
    <img src="../assets/kunai2.png" class="kunai" ref="kunai" />
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, onUpdated } from "vue"

const props = defineProps({
  delay: Number
})

// defineProps({
//   delay: Number
// })

const kunai = ref(null)
const x = ref(0)
const y = ref(0)
const showBlock = ref(false)

const currentTime = ref(null)
const newTime = ref(null)
const timeInterval = ref(null)

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
    currentTime.value = Date.now()
    console.log(currentTime.value)
  }, delay)
}

function getDelayAfterClick() {
  newTime.value = Date.now()
  timeInterval.value = newTime.value - currentTime.value
  showBlock.value = false
  console.log(`${timeInterval.value}ms`)
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
