<script setup>
import HomeEmpty from "@/components/home/HomeEmpty.vue";
import HomeList from "@/components/home/HomeList.vue";

import { ref, onMounted } from "vue";
import { supabase } from "@/lib/supabaseClient";

const searchValue = ref("");
const list = ref([]);
const errorValue = ref("");

onMounted(() => {
  getLsit();
});

const onClickSearch = async () => {
  const { data, error } = await supabase.from("table").select("*").like("title", `%${searchValue.value}%`);

  if (error) {
    errorValue.value = error;
  } else {
    list.value = data;
  }

  searchValue.value = "";
};

async function getLsit() {
  const { data } = await supabase.from("table").select();

  list.value = data;
}
</script>

<template>
  <div>
    <form class="form" @submit.prevent="onClickSearch">
      <input role="search" v-model="searchValue" type="text" placeholder="검색어를 입력하세요" />
      <button type="button" @click="onClickSearch">검색</button>
    </form>

    <div class="content">
      <component :is="!!list?.length ? HomeList : HomeEmpty" :lists="list" />
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
