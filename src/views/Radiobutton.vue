<template>
  <h1 class="heading-1">Radiobutton</h1>
  <h2 class="heading-2">Basic</h2>
  <div class="line line_block">
    <p>Selected Club: {{ selectedClub }}</p>
    <div v-for="club in foolbalClubs" :key="club.id">
      <radiobutton
        :label="club.name"
        :id="club.id"
        name="club"
        :value="club.name"
        v-model:checkedValue="selectedClub"
      />
    </div>
  </div>

  <h2 class="heading-2">Disabled</h2>
  <div class="line line_block">
      <radiobutton
        label="Radiobutton disabled"
        id="Radiobuttondisabled"
        name="Radiobutton disabled"
        :disabled="disabledRadio"
        value="Radiobutton disabled"
        v-model:checkedValue="disabledRadioChecked"
      />
    
  </div>
</template>
<script setup>
import { ref } from "vue";
import Radiobutton from "@/components/Radiobutton.vue";
const foolbalClubs = ref([
  { name: "CSKA Moskow", id: "f1" },
  { name: "Spartak Moskow", id: "f2" },
  { name: "Real Madrid", id: "f3" },
  { name: "Milan", id: "f4" },
]);
const selectedClub = ref('');
const disabledRadio=ref(true)
const disabledRadioChecked=ref("Radiobutton disabled")
</script>
<style lang=""></style>
