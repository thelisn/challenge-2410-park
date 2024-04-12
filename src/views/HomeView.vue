<script setup>
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
};
</script>

<template>
  <div>
    <form class="form" @submit.prevent="onClickSearch">
      <input v-model="searchValue" type="text" placeholder="검색어를 입력하세요" />
      <button type="button" @click="onClickSearch">검색</button>
    </form>

    <div class="content">
      <ul v-if="!!list.length" class="list">
        <li v-for="({ date, title, content }, index) of list" :key="index">
          <p>{{ date }}</p>
          <p>{{ title }}</p>
          <p>{{ content }}</p>
        </li>
      </ul>

      <div v-else class="empty">
        <p>없어요</p>
      </div>
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

.content {
  & .list {
    & li {
      display: flex;
      gap: 10px;
      padding-block: 10px;
    }
  }

  & .empty {
    text-align: center;
    color: #868a93;
    font-size: 14px;
  }
}
</style>
