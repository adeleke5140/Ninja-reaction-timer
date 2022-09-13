<template>
  <div class="result">
    <p>
      Reaction time: <span class="score">{{ score }}ms</span>
    </p>
    <p class="rank">{{ ninjaResult }}, shinobi-kun</p>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue"
const props = defineProps(["score"])

const ninjaResult = ref("")

function getNinjaResult(score) {
  console.log(score)
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
.result {
  font-family: "Asian Ninja";
}

.score {
  /* font-family: "Asian Ninja"; */
  color: #0faf87;
}

.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
  font-family: "Assassin Ninja";
  border: 1px solid #0faf87;
  padding: 1em;
  box-shadow: 3px 15px 8px -10px rgba(0, 0, 0, 0.3);
  border-top-left-radius: 37px 140px;
  border-top-right-radius: 23px 130px;
  border-bottom-left-radius: 110px 19px;
  border-bottom-right-radius: 120px 24px;
}
</style>
