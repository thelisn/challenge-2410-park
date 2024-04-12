<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <main id="main">
    <header>
      <div class="wrapper">
        <nav>
          <RouterLink to="/">Home</RouterLink>
          <RouterLink to="/about">About</RouterLink>
        </nav>
      </div>
    </header>

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

  & header {
    margin-bottom: 10px;

    & nav {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 20px;
    }
  }
}
</style>
