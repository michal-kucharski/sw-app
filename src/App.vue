<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/character-info">Character Info</router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>
import axios from 'axios';

const swapi = "https://swapi.dev/api/people/";

export default {
  data() {
    return {
      characterList: null,
    }
  },
  mounted() {
    axios.get(swapi).then(response => this.characterList = response);
  }
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
</style>
