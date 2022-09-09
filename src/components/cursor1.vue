<script setup>
import { ref, onMounted, onUnmounted } from "vue"

// const x = ref(0)
// const y = ref(0)
const cursor = ref(null)

function update(event) {
  cursor.value.style.top = event.pageY + "px"
  cursor.value.style.left = event.pageX + "px"
}

onMounted(() => window.addEventListener("mousemove", update))
onUnmounted(() => window.removeEventListener("mousemove", update))
</script>

<template>
  <div>
    <img
      src="../assets/kunai.png"
      alt="image of a kunai"
      class="cursor"
      ref="cursor"
    />
  </div>
</template>

<style>
.cursor {
  width: 20px;
  height: 20px;
  position: absolute;
  cursor: pointer;
  pointer-events: none;
  animation: spin 200ms linear infinite;
  transform: rotate(635deg);
}

/* @keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
} */
</style>
