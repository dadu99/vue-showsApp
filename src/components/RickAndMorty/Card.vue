<script setup>
    import {defineProps} from "vue"

    const {image, name } = defineProps([
        'image',
        'name',
    ])
</script>

<template>
  <NCard :bordered="false">
    <template #cover>
      <img :src="image">
    </template>
    <h3>{{ name }}</h3>
    <slot></slot>
  </NCard>
</template>

<style scoped>

.n-card {
    width: 200px;
    margin:10px 20px;

}
h3 {
    font-weight: 300;
    font-size: 27px;
}
.n-card img {
    height: 250px
}


</style>