<script setup>
    import { RouterLink } from 'vue-router';

    const props = defineProps({
        meal: Object
    })

</script>


<template>
    <li :key="meal.idMeal">
        <img :src="meal.strMealThumb" :alt="meal.strMeal">
        <div class="meal-content">
            <h3 class="meal-title">{{ meal.strMeal }}</h3>
            <p>{{ meal.strArea }} - {{ meal.strCategory }}</p>
            <router-link :to="{ name: 'Meal', params: { idMeal: meal.idMeal } }" class="detail-link">Recepta</router-link>
        </div>
    </li>
</template>

<style scoped>
    li {
        display: flex;

        height: auto;
        border-radius: 8px;
        overflow: hidden;

        border: 1px solid #403128;

        box-shadow: 5px 5px 2px 0px #40312875;
        background-color: #bdbc9b;      
        
        transition: all 200ms ease-in-out;

        cursor: pointer;

        min-height: 200px;;

    }

    li:hover {
        flex-direction: row;
        scale: 101%;
    }

    
    li:hover img {
        width: 20%;
    }


    li img {
        width: 50%;
        object-fit: cover;

        transition: all 300ms ease-in-out;


    }

    h3 {
        display: -webkit-box;
        -webkit-line-clamp: 3;      /* número de líneas */
        -webkit-box-orient: vertical;

        overflow: hidden;
    }


    .meal-content {
        display: flex;
        padding: 20px;

        justify-content: center;
        flex-direction: column;
        width: 100%;
        gap: 10px;
    }

    .meal-content p {
        font-size: 14px;
    }

    .meal-title {
        color: #403128;
    }

    .detail-link {
        margin-top:  10px;
        padding: 8px 20px;
        background-color: #d9d2b0;
        width: fit-content;
        border-radius: 4px;

        color: black;
        text-decoration: none;
        font-size: 14px;
    }

    .detail-link:hover {
        text-decoration: underline;
    }
</style>