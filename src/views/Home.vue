<script setup>
import { useFetch } from "@/composables/useFetch.js";
import { ref } from "vue";
import MealCard from "@/components/MealCard.vue";

const cerca = ref("chicken");
const url = ref(
  `https://www.themealdb.com/api/json/v1/1/search.php?s=${cerca.value}`
);

const { data, error, loading, fetchData } = useFetch(url);
</script>

<template>
  <div v-if="loading">Carregant...</div>
  <div v-else-if="error">{{ error }}</div>
  <div v-else>
    <ul v-if="data && data.meals">
      <meal-card v-for="meal in data.meals" :key="meal.idMeal" :data="data" />
    </ul>
  </div>
</template>

<style scoped>
  ul {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;

    gap: 30px;
  }
</style>
