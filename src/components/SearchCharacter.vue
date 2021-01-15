<template>
  <div class="search-container">
    <h2>Search for Star Wars characters</h2>
    <p v-if="emptySearch" class="text-danger">{{this.emptySearch}}</p>
    <p v-if="searchError" class="text-danger">{{this.searchError}}</p>
    <div class="search-bar">
        <b-input-group prepend="Type character name" class="mt-4">
          <b-form-input v-model="searchName" @keyup.enter="searchCharacter(searchName)"></b-form-input>
          <b-input-group-append>
            <b-button variant="success" @click="searchCharacter(searchName)">Search</b-button>
          </b-input-group-append>
      </b-input-group>
        <!-- <input type="text" v-model="searchName">
        <b-button variant="success" @click="searchCharacter(searchName)">Success</b-button> -->
    </div>

    <div class="character-list-container mt-3" v-if="filteredCharactersArray.length !== 0">
      <p class="text-white">Here is your characters list. Click the name to get specific informations.</p>
      <b-list-group class="list">
          <router-link to="/character-info" v-for="(item, index) in filteredCharactersArray" :key="item.url">
            <b-list-group-item :id="index" @click="getItemIndex" variant="dark" class="mt-4 list-item">{{item.name}}</b-list-group-item>    
          </router-link>
      </b-list-group>
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
          filteredCharactersArray: this.filteredCharactersList,
          itemIndex: null,
          emptySearch: undefined,
          searchError: undefined,
      }
    },
    props: {
    charactersList: Array,
    filteredCharactersList: Array,
    },
    methods: {
      searchCharacter:function(name) {
        if(!name) {
          this.emptySearch = 'You have to type something to search for the character!'
          return
        }
        this.filteredCharactersArray = [];
        this.emptySearch = undefined;
        this.searchError = undefined;
        this.charactersArray.forEach((item) => {
          if(item.name.toLowerCase().includes(name.toLowerCase())){
            this.filteredCharactersArray.push(item);            
          }
        })

        if(this.filteredCharactersArray.length === 0) {
            this.searchError = 'We cannot find character with such name! Try to type in another name'
            return
        }

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
  .character-list-container {
    background: rgb(2,0,36);
    background: linear-gradient(90deg, rgba(2,0,36,1) 0%, rgba(16,16,18,1) 0%, rgba(50,53,54,1) 30%, rgba(0,0,0,1) 50%);
    width: 90%;
    margin: auto;
    padding: 2% 4% 4%;
  }
  .list-item {
    width: 40%;
    margin: auto;
  }
  .text-white {
    color:white
  }
  @media(min-width: 768px) {
    .search-bar {
      width: 60%;
      margin: auto;
    }
  }
</style>