<script setup>
    import axios from "axios"
    import { watch, ref, onMounted, onUpdated } from "vue";
    import Card from "./Card.vue"

    const characters = ref(null);
    const page = ref(1);

    onMounted(async () => {
        console.log("component is mounted");
        const response = await axios.get("https://rickandmortyapi.com/api/character")
        console.log(response);
        characters.value = response.data.results
    })

    onUpdated(() => {
        console.log("component was updated");
            watch(page, async () => {
            const res = await axios.get(`https://rickandmortyapi.com/api/character/?page=${page.value}`);
            characters.value = res.data.results;
        })
    })

</script>

<template>
    <div class="container">
        <div v-if="characters" class="cards">
            <Card 
                v-for="character in characters" :key="character.id"
                :image="character.image"
                :name="character.name"
            >
                <p>{{character.location.name}}</p>
                <p>Status: {{ character.status }}</p>
                <p>Nr. episode: {{ character.episode.length }}</p>
            </Card>
        </div>
        <div v-else class="cards spinner">
            <NSpin size="large"/>
        </div>

        <p class="page-number">Current page number: {{ page }}</p>
        <div class="button-container">
            <button @click="page--">&lt</button>
            <button @click="page++">></button>
        </div>
    </div>
</template>

<style scoped>
.container {
    padding: 30px;
}
.cards {
    max-width: 1000px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    
}
.cards p {
    font-size: 18px;
}
.page-number {
    font-size: 16px;
    text-align: center;
    color: aliceblue;
    padding: 16px 0;
}
.jobs {
    display: flex;
    flex-wrap: wrap;
}
.button-container {
    display: flex;
    justify-content: center;
    padding-top: 30px
}
.button-container button {
    border: none;
    width: 50px;
    height: 50px;
    border-radius: 100%;
    margin: 0 5px;
    cursor: pointer;
}
.spinner {
    display: flex;
    align-items: center;
    justify-content: center;
}

</style>