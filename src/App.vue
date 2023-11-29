<script setup>
  import RickAndMortyCards from "./components/RickAndMorty/RickAndMortyCards.vue";

</script>


<template>
  <main>
    <h1>Hero</h1>
    <Suspense>
      <template #default>
        <RickAndMortyCards></RickAndMortyCards>
      </template>
      <template #fallback>
        <div>
          <p>Loading..</p>
        </div>
      </template>
    </Suspense>
  </main>
</template>

<style scoped>
</style>
