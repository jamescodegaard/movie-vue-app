<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="movie in movies">
      <h3>{{ movie.title }}</h3>
      <p>{{ movie.year }}</p>
      <button v-on:click="showMovies(movie)">More Info</button>
    </div>
    <dialog id="movie-details">
      <form method="dialog">
        <h3>{{ currentMovie.title }}</h3>
        <p>Released in {{ currentMovie.year }}</p>
        <p>Director: {{ currentMovie.year }}</p>
        <p>Plot: {{ currentMovie.plot }}</p>
        <button>Close</button>
      </form>
    </dialog>
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
      movies: [],
      currentMovie: {}
    };
  },
  created: function() {
    this.indexMovies();
  },
  methods: {
    indexMovies: function() {
      axios.get("/api/movies").then(response => {
        console.log("Movies:", response.data);
        this.movies = response.data;
      });
    },
    showMovies: function(movie) {
      console.log(movie);
      this.currentMovie = movie;
      document.querySelector("#movie-details").showModal();
    }
  }
};
</script>