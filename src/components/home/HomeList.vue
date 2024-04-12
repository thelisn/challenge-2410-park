<script setup>
defineProps(["lists"]);
</script>

<template>
  <ul class="list">
    <li v-for="({ date, title, content }, index) of lists" :key="index">
      <p>{{ date }}</p>
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
