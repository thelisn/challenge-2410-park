<script setup>
import { ref } from "vue";
import router from "@/router";

const inputValue = ref("");
const textAreaValue = ref("");

const onSubmit = () => {
  const koDtf = new Intl.DateTimeFormat("ko", { dateStyle: "long" });
  const date = koDtf.format(new Date());
  const obj = { date, title: inputValue.value, content: textAreaValue.value };
  const list = JSON.parse(localStorage.getItem("list")) ?? [];

  list.push(obj);

  localStorage.setItem("list", JSON.stringify(list));

  router.push("/");
};
</script>

<template>
  <form class="form" @submit.prevent="onSubmit">
    <input v-model="inputValue" type="text" placeholder="제목을 입력하세요" />
    <textarea v-model="textAreaValue"></textarea>

    <button @click="onSubmit" type="button">저장</button>
  </form>
</template>

<style scoped>
.form {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 20px;
  margin-bottom: 40px;
  padding: 20px;
}
</style>
