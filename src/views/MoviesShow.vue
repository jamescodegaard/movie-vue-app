<template>
  <div class="movies-show">
    <h3>{{ movie.title }}</h3>
    <p>Released: {{ movie.year }}</p>
    <p>Director: {{ movie.director }}</p>
    <p>{{ movie.plot }}</p>
    <router-link v-bind:to="`/movies/${movie.id}/edit`">Edit Movie</router-link>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      movie: {}
    };
  },
  created: function() {
    axios.get(`/api/movies/${this.$route.params.id}`).then(response => {
      this.movie = response.data;
    });
  },
  methods: {}
};
</script>