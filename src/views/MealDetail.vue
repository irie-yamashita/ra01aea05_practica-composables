<script setup>
import { useRoute } from 'vue-router';
import { useFetch } from '@/composables/useFetch.js';
import { ref } from 'vue';


const route = useRoute();

const url = ref(
    `www.themealdb.com/api/json/v1/1/lookup.php?i=${route.params.idMeal}`
);
console.log(url.value);

const { data, error, loading, fetchData } = useFetch(url);


</script>


<template>
  <div v-if="loading">
    <h1>Recepta</h1>
    <p>Loading...</p>
  </div>
  <div v-else-if="error">Error: {{ error }}</div>
    <div v-else>
    </div>

</template>
