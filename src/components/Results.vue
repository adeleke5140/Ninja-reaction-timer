<template>
  <div class="result">
    <p>
      Reaction time: <span class="score">{{ score }}</span
      >ms
    </p>
    <p class="rank" v-if="score < 600">{{ ninjaResult }}, shinobi-kun</p>
    <p class="rank" v-else>You are not a Shinobu yet. {{ ninjaResult }}</p>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue"
const props = defineProps(["score"])

const ninjaResult = ref("")

function getNinjaResult(score) {
  console.log(score, "function fired")
  if (score < 100) {
    ninjaResult.value = "You are worthy of being  sensei!"
  } else if (score > 100 && score <= 250) {
    ninjaResult.value = "Ninja Fingers"
  } else if (score > 250 && score <= 400) {
    ninjaResult.value = "Fast Fingers"
  } else if (score > 400 && score <= 600) {
    ninjaResult.value = "Slow"
  } else {
    ninjaResult.value = "You need to go back to the training ground!"
  }
}

onMounted(() => {
  console.log("result component mounted")
  getNinjaResult(props.score)
})
</script>

<style>
.result,
.score {
  font-family: "Assassin Ninja";
  font-family: "Asian Ninja";
}

.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>
