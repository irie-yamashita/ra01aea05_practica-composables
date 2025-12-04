<script setup>
import { useFetch } from '@/composables/useFetch.js';
import { ref } from 'vue';


const cerca = ref("chicken");
const url = ref(`https://www.themealdb.com/api/json/v1/1/search.php?s=${cerca.value}`);


const { data, error, loading, fetchData} = useFetch(url);

console.log(url.value)

</script>

<template>
  <h1>The Real Meal</h1>

  <div v-if="loading">Carregant...</div>
  <div v-else-if="error">{{ error }}</div>
  <div v-else>
    <ul v-if="data && data.meals">
      <li v-for="meal in data.meals">{{ meal.strMeal }}</li>
    </ul>
  </div>

  
</template>

<style scoped></style>
