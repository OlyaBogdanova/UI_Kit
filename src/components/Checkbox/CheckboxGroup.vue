<template>
  <div v-for="option in options" :key="options.id">
    <checkbox
      :name="name"
      :label="option.name"
      :value="option.name"
      :id="option.id"
      :checked="value.includes(option.id)"
      group
      @updateCheckboxGroup="check"
    />
  </div>
</template>
<script setup>
import Checkbox from "@/components/Checkbox/Checkbox.vue";
const props = defineProps({
  options: {
    type: Array,
    required: true,
    validator: (value) => {
      const hasNameKey = value.every((option) =>
        Object.keys(option).includes("name")
      );
      const hasIdKey = value.every((option) =>
        Object.keys(option).includes("id")
      );
      return hasNameKey && hasIdKey;
    },
  },
  name: {
    type: String,
    required: true,
  },
  value: {
    type: Array,
    required: true,
  },
});
const emits = defineEmits("update:value");

function check(params) {
  let updateValue = [...props.value];

  if(params.checked){
    updateValue.push(params.optionId)

  } else{
    updateValue.splice(updateValue.indexOf(params.optionId),1)
  }
  emits("update:value", updateValue)
}
</script>
<style lang="scss"></style>
