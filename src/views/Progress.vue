<template>
  <h1 class="heading-1">Progress</h1>
  <h2 class="heading-2">Progress Bar</h2>
  <div class="line line_block">
    <progress-bar max-width="500px" :percent="percentBar" color="warning" />
    <Button label="Add 10%" @click="addPercentBar" />
  </div>
  <h2 class="heading-2">Progress Bar Circle</h2>
  <div class="line line_block">
    <progress-circle :percent="percentBarCircle" color="danger" />
    <Button label="Subtract 10%" @click="removePercentBar" />
  </div>
</template>
<script setup>
import ProgressBar from "@/components/Progress/ProgressBar.vue";
import ProgressCircle from "@/components/Progress/ProgressCircle.vue";
import Button from "@/components/Button.vue";
import { ref } from "vue";
const percentBar = ref(45);
const percentBarCircle = ref(60);

function addPercentBar() {
  percentBar.value += 10;
  if (percentBar.value > 100) {
    percentBar.value = 100;
  }
}

function removePercentBar(){
    percentBarCircle.value -= 10;
    if (percentBarCircle.value<0) {
    percentBarCircle.value = 0;
  }
}
</script>
<style lang="scss" scoped></style>
