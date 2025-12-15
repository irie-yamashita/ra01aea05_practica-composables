<script setup>
    import { RouterLink } from 'vue-router';

    const props = defineProps({
        data: Object
    })

</script>


<template>
    <li v-for="meal in data.meals" :key="meal.idMeal">
        <img :src="meal.strMealThumb" :alt="meal.strMeal">
        <main>
            <h3 class="meal-title">{{ meal.strMeal }}</h3>
            <p>{{ meal.strArea }} - {{ meal.strCategory }}</p>
            <router-link :to="{ name: 'Meal', params: { idMeal: meal.idMeal } }" class="detail-link">Recepta</router-link>
        </main>
    </li>
</template>

<style scoped>
    li {
        display: flex;
        flex-direction: column;

        gap: 20px;

        border-radius: 8px;
        overflow: hidden;

        padding: 20px;
        border: 1px solid #403128;

        box-shadow: 5px 5px 2px 0px #40312875;

    }

    li img {
        width: 100%;
        object-fit: cover;

    }

    li main {
        display: flex;
        flex-direction: column;
        gap: 10px;

        width: 100%;
    }

    .meal-title {
        color: #403128;
    }

    .detail-link {
        padding: 5px 20px;
        background-color: #403128;
        width: fit-content;
        border-radius: 4px;

        color: black;
        text-decoration: none;
    }

    .detail-link:hover {

    }
</style>