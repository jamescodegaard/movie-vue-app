<template>
  <div class="movies-index">
    <h1>{{ message }}</h1>
    <router-link to="/movies/new">New Movie</router-link>
    <div v-for="movie in movies">
      <h3>{{ movie.title }}</h3>
      <p>{{ movie.year }}</p>
      <p>{{ movie.description }}</p>
    </div>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Movies",
      movies: []
    };
  },
  created: function() {
    axios.get("/api/movies").then(response => {
      this.movies = response.data;
    });
  },
  methods: {}
};
</script>