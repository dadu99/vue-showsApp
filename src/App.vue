<script setup>
  import RickAndMortyCards from "./components/RickAndMorty/RickAndMortyCards.vue";

</script>


<template>
    <h1 class="title">Rick & Morty </h1>
    <Suspense>
      <template #default>
        <RickAndMortyCards></RickAndMortyCards>
      </template>
      <template #fallback>
        <div class="cards spinner">
          <NSpin size="large"/>
        </div>
      </template>
    </Suspense>
</template>

<style scoped>
.title {
  padding: 20px;
  font-size: 70px;
  color: aliceblue;
  text-align: center;
}
</style>
