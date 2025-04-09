<template>
  <CardComponent :pelicula="pelicula" />
</template>

<script lang="ts" setup>
import CardComponent from './components/CardComponent.vue'

const pelicula = {
  id: 1,
  titulo: 'El Señor de los Anilloss',
  anio: 2001,
  genero: 'Fantasía',
  director: 'Peter Jackson',
  portada: 'https://via.placeholder.com/300x400', 
  likes: 5
}

</script>

<style scoped>

</style>
