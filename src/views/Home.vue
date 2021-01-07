<template>
  <div class="home">
    <h1>Search for your favourites Star Wars characters</h1>
    <SearchCharacter/>
    <CharacterList/>
  </div>
</template>

<script>
// @ is an alias to /src
import SearchCharacter from '@/components/SearchCharacter.vue'
import CharacterList from '@/components/CharacterList.vue'

export default {
  name: 'Home',
  components: {
    SearchCharacter,
    CharacterList,
  }
}
</script>
