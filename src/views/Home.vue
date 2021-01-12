<template>
  <div class="home">
    <h1>Search for your favourites Star Wars characters</h1>
    <SearchCharacter @itemIndex="itemIndex = $event" @filteredCharacters="filteredCharactersArray = $event" :charactersList="charactersArray"/>
  </div>
</template>

<script>
// @ is an alias to /src
import SearchCharacter from '@/components/SearchCharacter.vue'

export default {
  name: 'Home',
  components: {
    SearchCharacter,
  },
  data() {
    return {
      charactersArray: this.charactersList,
      filteredCharactersArray: [],
      itemIndex: null
    }
  },
  props: {
    charactersList: Array,
  },
}
</script>
