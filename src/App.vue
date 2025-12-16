<script setup>
import { RouterView } from 'vue-router';
import NavigationBar from './components/NavigationBar.vue';

</script>

<template>

  <main>
    <header>
      <h1>Meals DB</h1>
      <navigation-bar></navigation-bar>
    </header>
    <router-view></router-view>
  </main>
</template>

<style scoped>

  h1 {
    color: #d9d2b0;
  }

  main {
    display: flex;
    flex-direction: column;
    gap: 20px;

    padding-top: 50px;
    padding-bottom: 50px;

  }

  header {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
</style>
