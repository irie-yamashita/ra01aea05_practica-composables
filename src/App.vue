<script setup>
import { RouterView } from 'vue-router';
import NavigationBar from './components/NavigationBar.vue';

</script>

<template>

  <main>
    <header>
      <h1>The Real Meal</h1>
      <navigation-bar></navigation-bar>
    </header>
    <router-view></router-view>
  </main>
</template>

<style scoped>

  h1 {
    color: #403128;
  }

  main {
    display: flex;
    flex-direction: column;
    gap: 20px;

    padding-top: 50px;
  }

  header {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
</style>
