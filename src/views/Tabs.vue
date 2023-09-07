<template>
  <h1 class="heading-1">Tabs</h1>
  <Tab
    :names="tabs"
    :selectedTab="selectedTab"
    @update:selectedTab="updateSelectedTab"
  >
    <div v-if="selectedTab==='About'">Lorem ipsum dolor sit amet.</div>
    <div v-if="selectedTab==='Vue'">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Delectus, est.
    </div>
    <div v-if="selectedTab==='React'">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Corporis modi
      dolore consequatur non quam doloribus?
    </div>
  </Tab>
</template>
<script setup>
import { ref, computed } from "vue";
import Tab from "@/components/Tab.vue";

const tabs = [
  {
    name: "About",
    label: "О проекте",
  },
  {
    name: "Vue",
    label: "Про Vue",
  },
  {
    name: "React",
    label: "Про React",
  },
];

const selectedTab = ref("Vue");

function updateSelectedTab(selTab) {
  selectedTab.value = selTab;
}
</script>
<style lang="scss" scoped></style>
