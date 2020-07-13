<template>
  <div id="app">
    <div id="header">
      <div class="inner">
        <router-link class="button" to="/">Home</router-link> | 
        <router-link class="button" to="/movies">Index</router-link> |
        <router-link class="button" to="/signup">Signup</router-link> |
        <router-link class="button" to="/login">Login</router-link> |
        <router-link class="button" to="/logout">Logout</router-link> |
      </div>
    </div>
    <router-view/>
    <footer id="footer">
      <div class="inner">
      </div>
    </footer>
  </div>
</template>

<style>
</style>
