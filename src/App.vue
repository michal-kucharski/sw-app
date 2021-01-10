<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/character-info">Character Info</router-link>
    </div> -->
    <img v-if="!characterArray" src="https://cdn.dribbble.com/users/361263/screenshots/3051905/imperial_emblem.gif" alt="">
    <router-view v-if="characterArray" :characterList="characterArray"/>
  </div>
</template>

<script>
import axios from 'axios';

const swapi = "https://swapi.dev/api/people/";

export default {
  data() {
    return {
      characterArray: null,
    }
  },
  mounted() {
    let people = [];
    axios.get(swapi)
        .then(response => {
            people = response.data.results;
            return response.data.count;
        })
        .then(count => {
            const numberOfPagesLeft = Math.ceil((count - 1) / 10);
            let promises = [];
            for (let i = 2; i <= numberOfPagesLeft; i++) {
                promises.push(axios(`https://swapi.dev/api/people?page=${i}`));
            }
            return Promise.all(promises);
        })
        .then(response => {
            people = response.reduce((acc, data) => [...acc, ...data.data.results], people);
            this.characterArray = people;
        })
        .catch(error => console.log(error.response));
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
</style>
