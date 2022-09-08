<template>
  <div class="block" @mousemove="handleKunaiPosition">
    Click me
    <img src="../assets/kunai2.png" class="kunai" ref="kunai" />
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue"

defineProps({
  delay: Number
})

const kunai = ref(null)
const x = ref(0)
const y = ref(0)

function handleKunaiPosition(e) {
  x.value = e.offsetX
  y.value = e.offsetY

  kunai.value.style.top = y.value + "px"
  kunai.value.style.left = x.value + "px"
}
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
