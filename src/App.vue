<template>
  <div id="app">
    <img v-if="!charactersArray" src="https://cdn.dribbble.com/users/361263/screenshots/3051905/imperial_emblem.gif" alt="loading" class="img-responsive">
    <router-view v-if="charactersArray" :charactersList="charactersArray"/>
  </div>
</template>

<script>
import axios from 'axios';

const swapi = "https://swapi-deno.azurewebsites.net/api/people/";

export default {
  data() {
    return {
      charactersArray: null,
    }
  },
  mounted() {
      let people = [];

      axios.get(swapi).then(response => {
        people = response.data;
        this.charactersArray = people;
      })
    },
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #111;
  max-width: 1280px;
  margin: 0 auto;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
.img-responsive {
  max-width: 100%;
}
</style>
