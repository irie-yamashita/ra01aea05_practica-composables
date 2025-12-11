<script setup>
import { RouterView, RouterLink } from 'vue-router';
</script>

<template>

  <main>
    <h1>The Real Meal</h1>
    <router-link :to="{name: 'Home'}"">Home</router-link>
  
  
    <router-view></router-view>
  </main>
</template>

<style scoped></style>
