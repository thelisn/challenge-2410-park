<script setup>
import TheHeader from "@/layouts/TheHeader.vue";
import { RouterView } from "vue-router";
</script>

<template>
  <main id="main">
    <TheHeader />
    <RouterView />
  </main>
</template>

<style scoped>
#main {
  width: 100%;
  height: 100dvh;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
