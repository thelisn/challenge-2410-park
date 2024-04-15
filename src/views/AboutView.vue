<script setup>
import { ref } from "vue";
import { supabase } from "@/lib/supabaseClient";
import router from "@/router";

const inputValue = ref("");
const textAreaValue = ref("");
const endDateValue = ref(null);

const errorValue = ref("");

const onTextAreaKeyPress = (e) => {
  if (e.which === 13 && !e.shiftKey) {
    e.preventDefault();

    const newEvent = new Event("submit", { cancelable: true });
    e.target.form.dispatchEvent(newEvent);
  }
};

const onSubmit = async () => {
  const obj = { title: inputValue.value, content: textAreaValue.value, end_date: endDateValue.value };
  const { error } = await supabase.from("table").insert(obj);

  if (error) {
    errorValue.value = error;
  } else {
    router.push("/");
  }
};
</script>

<template>
  <form class="form" @submit.prevent="onSubmit">
    <input v-model="inputValue" type="text" placeholder="제목을 입력하세요" />
    <input v-model="endDateValue" type="date" />
    <textarea v-model="textAreaValue" autocomplete="off" type="text" @keypress="onTextAreaKeyPress"></textarea>

    <button @click="onSubmit" type="button">저장</button>
  </form>

  <p class="error" v-show="errorValue">{{ errorValue }}</p>
</template>

<style scoped>
.form {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 20px;
  padding: 20px;
}

.error {
  color: #ff6060;
  font-size: 14px;
}
</style>
