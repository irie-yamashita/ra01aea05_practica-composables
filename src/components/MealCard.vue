<script setup>
    import { RouterLink } from 'vue-router';

    const props = defineProps({
        data: Object
    })

</script>


<template>
    <li v-for="meal in data.meals" :key="meal.idMeal">
        <img :src="meal.strMealThumb" :alt="meal.strMeal">
        <h3>{{ meal.strMeal }}</h3>
        <p>{{ meal.strArea }} - {{ meal.strCategory }}</p>
        <router-link :to="{ name: 'Meal', params: { idMeal: meal.idMeal } }">Recepta</router-link>
    </li>
</template>

<style scoped>
    li {
        display: flex;
        flex-direction: column;

        border-radius: 8px;
        overflow: hidden;

        padding: 20px;
        border: 1px solid gray;

    }

    li img {
        width: 100%;
        object-fit: cover;

    }
</style>