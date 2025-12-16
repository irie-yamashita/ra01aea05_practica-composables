<script setup>
import { useRoute } from "vue-router";
import { useFetch } from "@/composables/useFetch.js";
import { ref, watch } from "vue";

const route = useRoute();

const url = ref(
  `https://www.themealdb.com/api/json/v1/1/lookup.php?i=${route.params.idMeal}`
);

let { data, error, loading, fetchData } = useFetch(url);

watch(
  () => route.params.idMeal,
  (newId) => {
    url.value = newId;
    fetchData(newId);
  }
);


</script>

<template>
  <div v-if="loading">
    <h1>Recepta</h1>
    <p>Loading...</p>
  </div>
  <div v-else-if="error">
    <p>{{ error }}</p>
  </div>
  <div v-else>
    <div v-if="data && data.meals && Array.isArray(data.meals)">
      <div class="meal-container">
        <img :src="data.meals[0].strMealThumb" :alt="data.meals[0].strMeal" />
        <div class="info-container">
          <h1>{{ data.meals[0].strMeal }}</h1>
          <section class="instructions-section">
            <h2>Instruccions</h2>
            <p>{{ data.meals[0].strInstructions }}</p>
          </section>
        </div>
      </div>
    </div>
    <div v-else>
      <p>No hi ha dades</p>
    </div>
  </div>
</template>

<style scoped>
.meal-container {
  display: flex;
  gap: 30px;
}

.meal-container img {
  width: 40%;
  object-fit: contain;
  border-radius: 8px;

  box-shadow: 5px 5px 2px 0px #40312875;


}


.info-container {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

h1 {
  color: #d9d2b0;
  font-size: 26px;
}

.instructions-section {
  background-color: #bdbc9b;
  padding: 20px;
  border-radius: 4px;
}

h2 {
  font-size: 20px;
  margin-bottom: 10px;
}
</style>
