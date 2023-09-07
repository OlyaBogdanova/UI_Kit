<template>
  <h1 class="heading-1">Table</h1>
  <base-table
    :head="tableHeads"
    :columnsTemplates="tableSizeColumns"
    @changeSortingFiled="changeSortingFiled"
  >
    <table-row
      v-for="book in booksSorting"
      :key="book.id"
      :bgRow="book.bg"
      :columnsTemplates="tableSizeColumns"
    >
      <table-column :columnTitle="tableHeads[0]">{{ book.id }}</table-column>
      <table-column :columnTitle="tableHeads[1]">{{
        book.author
      }}</table-column>
      <table-column :columnTitle="tableHeads[2]">{{ book.title }}</table-column>
      <table-column :image="true" :srcImage="book.image"></table-column>
      <table-column><Button label="Read Online"></Button></table-column>
    </table-row>
  </base-table>
</template>
<script setup>
import { ref, computed } from "vue";
import BaseTable from "@/components/Table/BaseTable.vue";
import TableRow from "@/components/Table/TableRow.vue";
import TableColumn from "@/components/Table/TableColumn.vue";
import Button from "@/components/Button.vue";
const tableHeads = ["Id", "Author", "Title", "Cover", ""];
const tableSizeColumns = "50px 1fr 2fr 150px 140px";
const sortField = ref("id");
const typeSort = ref("asc");

const booksSorting = computed(() => {
  return books.value.sort((a, b) => {
    let modifier = 1;
    if (typeSort.value === "desc") modifier = -1;
    if (a[sortField.value] < b[sortField.value]) return -1 * modifier;
    if (a[sortField.value] > b[sortField.value]) return 1 * modifier;
    return 0;
  });
});

function changeSortingFiled(name) {
  if (sortField.value === name) {
    typeSort.value = typeSort.value === "asc" ? "desc" : "asc";
  } else {
    sortField.value = name;
  }
}
const books = ref([
  {
    id: 1,
    author: "Dmitry Glukhovsky",
    title: "Metro 2033",
    image: "https://cv9.litres.ru/pub/c/cover_max1500/128391.jpg",
    bg: "#FFA26B",
  },
  {
    id: 12,
    author: "James Clear",
    title: "Atomic Habits: An Easy",
    image:
      "https://m.media-amazon.com/images/P/0735211299.01._SCLZZZZZZZ_SX500_.jpg",
    bg: "#00C48C",
  },
  {
    id: 2,
    author: "J. K. Rowling",
    title: "Harry Potter and the Order of the Phoenix",
    image:
      "https://img4.labirint.ru/rc/3c7f70276f733664f56f67b2ae5e66e0/363x561q80/books27/263508/cover.jpg?1683890702",
    bg: "#00C48C",
  },
]);
</script>
<style lang="scss" scoped></style>
