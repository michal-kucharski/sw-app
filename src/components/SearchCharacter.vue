<template>
  <div class="search-container">
    <div class="search-bar">
        <input type="text" v-model="searchName">
        <button @click="searchCharacter(searchName)">Search</button>
    </div>
    <div class="character-list-container">
      <ul>
          <router-link to="/character-info" v-for="(item, index) in filteredCharactersArray" :key="item.url">
            <li :id="index" @click="getItemIndex" >{{item.name}}</li>        
          </router-link>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
    name: 'SearchCharacter',
    data() {
      return{
          charactersArray: this.charactersList,
          searchName: '',
          filteredCharactersArray: [],
          itemIndex: null,
      }
    },
    props: {
    charactersList: Array,
    },
    methods: {
      searchCharacter:function(name) {
        this.filteredCharactersArray = [];
        this.charactersArray.forEach((item) => {
          if(item.name.toLowerCase().includes(name.toLowerCase())){
            this.filteredCharactersArray.push(item);            
          }
        })
        this.$emit("filteredCharacters", this.filteredCharactersArray); 
        this.$parent.$emit("filteredCharacters", this.filteredCharactersArray)      
      },
      getItemIndex: function(e) {
        this.itemIndex = parseInt(e.target.id);
        this.$emit("itemIndex", this.itemIndex);
        this.$parent.$emit("itemIndex", this.itemIndex)      
      }
    }
}
</script>

<style scoped>
  ul {
      width: 60%;
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
  @media(min-width: 768px) {
    ul {
      width: 40%
    }
  }
</style>