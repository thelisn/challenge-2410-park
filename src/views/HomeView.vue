<script setup>
import HomeEmpty from "@/components/home/HomeEmpty.vue";
import HomeList from "@/components/home/HomeList.vue";

import { ref, onMounted, computed } from "vue";

const searchValue = ref("");
const list = ref([]);

const storageList = computed(() => JSON.parse(localStorage.getItem("list")));

onMounted(() => {
  list.value = storageList.value;
});

const onClickSearch = () => {
  const filterList = storageList.value.filter((v) => v?.title.includes(searchValue.value));
  list.value = filterList;

  searchValue.value = "";
};
</script>

<template>
  <div>
    <form class="form" @submit.prevent="onClickSearch">
      <input v-model="searchValue" type="text" placeholder="검색어를 입력하세요" />
      <button type="button" @click="onClickSearch">검색</button>
    </form>

    <div class="content">
      <component :is="!!list.length ? HomeList : HomeEmpty" :lists="list" />
    </div>
  </div>
</template>

<style scoped>
.form {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
  margin-bottom: 40px;
  padding: 20px;
  border-bottom: 1px solid red;
}
</style>
