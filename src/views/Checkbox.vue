<template>
  <h1 class="heading-1">Checkbox</h1>
  <h2 class="heading-2">Checkbox active</h2>
  <div class="line">
    <checkbox
      label="Checkbox Active"
      id="checkboxActive"
      name="checkboxActive"
      value="I like it!"
      v-model:checked="checkboxActive"
    />
  </div>
  <h2 class="heading-2">Checkbox disabled</h2>
  <div class="line">
    <checkbox
      label="Checkbox Disabled"
      id="checkboxdisabled"
      name="checkboxdisabled"
      value="I like it!"
      :disabled="checkboxDisabled"
      v-model:checked="checkboxDisabledChecked"
    />
  </div>
  <h2 class="heading-2">Checkbox Group</h2>
  <div class="line line_block">
    <p>Selected Heroes: {{ selectedHeroes }}</p>
    <checkbox-group
      :options="listOfHeroes"
      name="heroes"
      v-model:value="selectedHeroes"
    />
  </div>

  <h2 class="heading-2">Switch</h2>
  <div class="line line_block">
    <p>Switch: {{ switchProffesilonal }}</p>
    <checkbox
      label="I am a professional"
      id="switch"
      name="switch"
      value="I am a professional"
      type="switch"
      v-model:checked="switchProffesilonal"
    />
  </div>
</template>
<script setup>
import Checkbox from "@/components/Checkbox/Checkbox.vue";
import CheckboxGroup from "@/components/Checkbox/CheckboxGroup.vue";
import { ref } from "vue";

const checkboxActive = ref(true);
const checkboxDisabled = ref(true);
const checkboxDisabledChecked = ref(true);
const switchProffesilonal = ref(false);

const listOfHeroes = ref([
  { id: "h1", name: "Spider Man" },
  { id: "h2", name: "Batman" },
  { id: "h3", name: "Tor" },
  { id: "h4", name: "Loki" },
]);
const selectedHeroes = ref(["h1"]);
</script>
<style lang="scss" scoped>
.line {
  display: flex;
  margin-bottom: 20px;
  flex-wrap: wrap;

}
</style>
