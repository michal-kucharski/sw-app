<template>
  <div class="home">
    <SearchCharacter @itemIndex="itemIndex = $event" @filteredCharacters="filteredCharactersArray = $event" :charactersList="charactersArray" :filteredCharactersList="filteredCharactersArray"/>
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
      filteredCharactersArray: this.filteredArray,
      itemIndex: null
    }
  },
  props: {
    charactersList: Array,
    filteredArray: Array,
  },
}
</script>
