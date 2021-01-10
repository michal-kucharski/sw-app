<template>
  <div class="character-list-container">
    <ul>
        <router-link to="/character-info" v-for="item in characterArray" :key="item.url">
          <li>{{item.name}}</li>        
        </router-link>
    </ul>
  </div>
</template>

<script>
export default {
    name: 'CharacterList',
    data() {
        return{
            characterArray: this.characterList,
        }
    },
    props: {
    characterList: Array,
    },
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