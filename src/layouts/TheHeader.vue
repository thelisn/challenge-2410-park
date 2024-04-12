<script setup></script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
    </nav>
  </header>
</template>

<style>
header {
  margin-bottom: 10px;

  & nav {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 20px;

    .router-link-active {
      background-color: red;
    }
  }
}
</style>
