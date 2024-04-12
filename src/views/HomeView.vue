<script setup>
import { ref, onMounted } from "vue";

const searchValue = ref("");
const list = ref([]);

const onClickSearch = () => {};

onMounted(() => {
  const _list = JSON.parse(localStorage.getItem("list"));
  list.value = _list;
});
</script>

<template>
  <div>
    <div>
      <form @submit.prevent="onClickSearch">
        <input v-model="searchValue" type="text" placeholder="검색어를 입력하세요" />
        <button type="button" @click="onClickSearch">검색</button>
      </form>
    </div>

    <ul v-if="list.length">
      <li v-for="({ date, title, content }, index) of list" :key="index">
        <div>{{ date }}</div>
        <div>{{ title }}</div>
        <div>{{ content }}</div>
      </li>
    </ul>

    <div v-else>없어용~</div>
  </div>
</template>

<style scoped>
form {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
  padding: 20px;
}
</style>
