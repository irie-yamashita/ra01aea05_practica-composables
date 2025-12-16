
<script setup>
import { ref } from 'vue';

let q = ref('');

const emit = defineEmits(['search-recipe']);

const searchRecipe = () => {
    emit('search-recipe', q.value);
    q.value = '';
};

</script>

<template>

    <div class="search-bar-container">
        <input type="text" name="q" id="q" placeholder="Cercar una recepta" v-model="q">
        <button @click="searchRecipe">Buscar</button>
    </div>

</template>

<style scoped>
.search-bar-container {
    display: flex;
    align-items: center;
    gap: 20px;

    justify-self: end;
}

input {
    border-bottom: 1px solid #403128;
    color: #d9d2b0;
    
    padding: 5px 10px;
}

input:focus-visible {
    background-color: rgba(255, 255, 255, 0.212);
    outline: none;

}

button {
    background-color: #d9d2b0;
    padding: 5px 20px;
    border-radius: 4px;

    transition: all ease-in-out 100ms;
}

button:hover {
    filter: brightness(110%);
    scale: 105%;
}


</style>