<template>
<div class="container">
  <h2 class="uppercase">Character information card</h2>
  <div class="character-info-container">
    <h2>Name: {{filteredCharactersArray[itemIndex].name}}</h2>
    <p>Height: {{filteredCharactersArray[itemIndex].height}}</p>
    <p>Weight: {{filteredCharactersArray[itemIndex].mass}}</p>
    <p>Skin color: {{filteredCharactersArray[itemIndex].skin_color}}</p>
    <p>Hair color: {{filteredCharactersArray[itemIndex].hair_color}}</p>
    <p>Gender: {{filteredCharactersArray[itemIndex].gender}}</p>
    <p>Homeworld: {{filteredCharactersArray[itemIndex].homeworld}}</p>
  </div>
</div>
</template>

<script>

export default {
    name: 'CharacterInfo',
    data() {
      return {
        }
      },
    computed: {
        filteredCharactersArray(){
          return this.$store.state.filteredCharactersArray;
        },
        itemIndex(){
          return this.$store.state.itemIndex;
        },
    }
  }
</script>

<style scoped>
  .uppercase {
    text-transform: uppercase;
  }
  .character-info-container {
    margin: 10% auto;
    background: rgb(37, 37, 37);
    color: whitesmoke;
    box-shadow: 10px 5px 5px rgb(37, 37, 37);
  }
</style>
