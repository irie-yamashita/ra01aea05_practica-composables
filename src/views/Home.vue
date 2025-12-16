<script setup>
import { useFetch } from "@/composables/useFetch.js";
import { ref, watch } from "vue";
import MealCard from "@/components/MealCard.vue";
import SearchBar from "@/components/SearchBar.vue";

const cerca = ref("veg");
const url = ref(
  `https://www.themealdb.com/api/json/v1/1/search.php?s=${cerca.value}`
);

const { data, error, loading, fetchData } = useFetch(url);

const handleSearchRecipe = (q) => {
  cerca.value = q;
  console.log('click')
}

watch(
  cerca,
  (newValue) => {
    url.value = `https://www.themealdb.com/api/json/v1/1/search.php?s=${newValue}`;
    fetchData();
    console.log(url);
  },
);

console.log(url.value)

</script>

<template>
  <search-bar @search-recipe="handleSearchRecipe"></search-bar>

  <div v-if="loading">Carregant...</div>
  <div v-else-if="error">{{ error }}</div>
  <div v-else>
    <ul v-if="data && data.meals">
      <meal-card v-for="meal in data.meals" :key="meal.idMeal" :meal="meal" />
    </ul>
    <p v-else class="info-message">
      NO HI HA RECEPTES AMB '{{ cerca }}' :/
    </p>
  </div>
</template>

<style scoped>
  ul {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 30px;
  }

  .info-message {
    margin-top: 20px;
    font-weight: bold;
    text-align: center;
    color: #d9d2b0;
  }
</style>
