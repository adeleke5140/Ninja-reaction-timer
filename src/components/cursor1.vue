<template>
  <div>
    <div class="cursor" ref="cursor"></div>
  </div>
</template>

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

<style scoped>
.cursor {
  width: 20px;
  height: 20px;
  /* border: 0.5px solid white; */
  border-radius: 50%;
  position: absolute;
  cursor: pointer;
  transform: translate(-50%, -50%);
  transition: border 300ms ease;
  pointer-events: none;
  background: url("../assets/shuriken.svg");
  animation: spin 100ms linear infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
