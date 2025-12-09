<script setup>
import { useFetch } from "@/composables/useFetch.js";
import { RouterLink } from "vue-router";
import { ref } from "vue";

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
      <li v-for="meal in data.meals" :key="meal.idMeal">
        <h3>{{ meal.strMeal }}</h3>
        <p>{{ meal.strArea }} - {{ meal.strCategory }}</p>
        <router-link :to="{ name: 'Meal', params: { idMeal: meal.idMeal } }">Recepta</router-link>
      </li>
    </ul>
  </div>
</template>
