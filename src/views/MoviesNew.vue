<template>
  <div class="movies-new">
    <form v-on:submit.prevent="createMovie()">
      <h1>Login</h1>
      <ul>
        <li class="text-danger" v-for="error in errors">{{ error }}</li>
      </ul>
      <div class="form-group">
        <label>Title:</label>
        <input type="text" class="form-control" v-model="newTitle">
      </div>
      <div class="form-group">
        <label>Year:</label>
        <input type="text" class="form-control" v-model="newYear">
      </div>
      <div class="form-group">
        <label>Plot:</label>
        <input type="text" class="form-control" v-model="newPlot">
      </div>
      <div class="form-group">
        <label>Director:</label>
        <input type="text" class="form-control" v-model="newDirector">
      </div>
      <div class="form-group">
        <label>English?</label>
        <input type="checkbox" class="form-control" v-model="newEnglish">
      </div>
      <input type="submit" class="btn btn-primary" value="Submit">
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      newTitle: "",
      newYear: "",
      newPlot: "",
      newDirector: "",
      newEnglish: "",
      errors: []
    };
  },
  methods: {
    createMovie: function() {
      var params = {
        title: this.newTitle,
        year: this.newYear,
        plot: this.newPlot,
        director: this.newDirector,
        english: this.newEnglish
      };
      axios
        .post("/api/movies", params)
        .then(response => {
          console.log("New Recipe:", response.data);
          this.$router.push("/movies");
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>