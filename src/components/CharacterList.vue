<template>
  <div class="character-list-container">
      <ul>
        <router-link to="/character-info">
          <li>Luke Skywalker</li>        
        </router-link>  
        <router-link to="/character-info">
          <li>Anakin Skywalker</li>        
        </router-link>  
          <li>Thrawn</li>
          <li>Jabba</li>
          <li>Grogu</li>
          <li>Mandalorian</li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'CharacterList',
}
</script>

<style scoped>
    ul {
        width: 20%;
        margin: 0 auto;
        padding-inline-start: 0;
        text-transform: uppercase;
    }
    li {
        background: #eee;
        list-style-type: none;
        border: 1px solid black;
        padding: 10px;
        margin: 10px auto;
    }
    ul a {
        text-decoration: none;
        color: black
    }
</style>