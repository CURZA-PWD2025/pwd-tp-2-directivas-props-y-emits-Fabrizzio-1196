<template>
  <div>
    <h1>Películas</h1>
    <div class="movies-container">
      <div class="card" v-for="movie in movies" :key="movie.id">
        <img :src="movie.portada" :alt="`Portada de ${movie.titulo}`" />
        <div class="card-content">
          <h2>{{ movie.titulo }}</h2>
          <p><strong>Director:</strong> {{ movie.director }}</p>
          <p><strong>Año:</strong> {{ movie.anio }}</p>
          <p><strong>Género:</strong> {{ movie.genero }}</p>
          <p><strong>Likes:</strong> {{ movie.likes }}</p>
          <button @click="toggleLike(movie.id)">
            {{ likedMovies.has(movie.id) ? 'Quitar Like' : 'Dar Like' }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref, defineEmits } from 'vue'
import { movies } from '../movies'

const emit = defineEmits(['update_likes'])

const likedMovies = ref<Set<number>>(new Set()) 

function toggleLike(movieId: number) {
  const movie = movies.find(m => m.id === movieId)

  if (!movie) return

  if (likedMovies.value.has(movieId)) {
    likedMovies.value.delete(movieId)
    movie.likes--
  } else {

    likedMovies.value.add(movieId)
    movie.likes++
  }

  emit('update_likes', { id: movieId, likes: movie.likes })
}
</script>

<style scoped>
.card {
  border: 1px solid #ddd;
  padding: 1rem;
  border-radius: 8px;
  max-width: 300px;
  box-shadow: 2px 2px 10px rgb(245, 241, 241);
}
.card img {
  width: 100%;
  border-radius: 4px;
}
.card-content button {
  margin-top: 1rem;
  padding: 0.5rem 1rem;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}
.card-content button:hover {
  background-color: #0056b3;
}
</style>