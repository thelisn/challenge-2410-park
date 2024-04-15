<script setup>
defineProps(["lists"]);
</script>

<template>
  <ul class="list">
    <li v-for="({ end_date, started_date, title, content }, index) of lists" :key="index">
      <p>{{ started_date }} ~ {{ end_date }}</p>
      <p>{{ title }}</p>
      <p>{{ content }}</p>
    </li>
  </ul>
</template>

<style scoped>
.list {
  & li {
    display: flex;
    gap: 10px;
    padding-block: 10px;

    & p {
      white-space: pre-wrap;
    }
  }
}
</style>
