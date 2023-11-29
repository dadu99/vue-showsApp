<script setup>
import axios from "axios"
import { ref } from 'vue';

const response = await axios.get("https://rickandmortyapi.com/api/character");
console.log(response);




</script>


<template>
    <div>
        <h1>Rick and morty cards</h1>
        <p>{{ response }}</p>
    </div>
</template>