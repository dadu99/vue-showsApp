<script setup>
import axios from "axios"
import { ref } from 'vue';

const response = await axios.get("https://rickandmortyapi.com/api/character/");
console.log(response.data.results);


</script>


<template>
    <div>
        <h1>Rick and Morty cards</h1>
        
    </div>
</template>