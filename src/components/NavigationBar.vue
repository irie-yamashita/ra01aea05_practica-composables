<script setup>
    import {  RouterLink } from 'vue-router';
</script>

<template>
    <router-link :to="{name: 'Home'}" class="link">Home</router-link>
</template>

<style>
    .link {
        color: whitesmoke;
        text-decoration: none;

        font-size: 14px;
    }

    .link:hover {
        color: #403128;
        text-decoration: underline;
    }

    .link:active {
        color: whitesmoke;
        text-decoration: none;
    }
</style>