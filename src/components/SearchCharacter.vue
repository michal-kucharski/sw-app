<template>
  <div class="search-container">
    <div class="search-bar">
        <input type="text" v-model="searchName">
        <button @click="searchCharacter(searchName)">Search</button>
    </div>
    <div class="character-list-container">
      <!-- <ul>
          <router-link to="/character-info" v-for="(item, index) in filteredCharactersArray" :key="item.url" @click="getItemIndex" :id="index">
            <li>{{item.name}}</li>        
          </router-link>
      </ul> -->
    </div>
    <ul>
      <li v-for="(item, index) in filteredCharactersArray" :key="item.url" @click="getItemIndex" :id="index">{{item.name}}</li>   
    </ul>
  </div>
</template>

<script>

export default {
    name: 'SearchCharacter',
    data() {
      return{
          charactersArray: this.charactersList,
          searchName: '',
      }
    },
    computed: {
        filteredCharactersArray(){
          return this.$store.state.filteredCharactersArray;
        },
        itemIndex(){
          return this.$store.state.itemIndex;
        },
      },  
    props: {
    charactersList: Array,
    },
    methods: {
      searchCharacter:function(name) {
        this.$store.state.filteredCharactersArray = [];
        this.charactersArray.forEach((item) => {
          if(item.name.toLowerCase().includes(name.toLowerCase())){
            console.log(this.$store.state.filteredCharactersArray);
            this.$store.state.filteredCharactersArray.push(item);
          }
        })
      },
      getItemIndex: function(e) {
        this.$store.state.itemIndex = e.target.id;
        console.log(this.$store.state.itemIndex);         
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