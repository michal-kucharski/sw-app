<template>
<div class="container">
  <router-link to="/">Return to character search</router-link>
  <h2 class="uppercase">Character information card</h2>
  <div class="row character-info-container">
    <div class="col-sm-12">
      <h2>Name: {{filteredCharactersArray[itemIndex].name}}</h2>
    </div>
    <div class="col-sm-6">
      <p>Height: {{filteredCharactersArray[itemIndex].height}}</p>
    </div>
    <div class="col-sm-6">
        <p>Weight: {{filteredCharactersArray[itemIndex].mass}}</p>
    </div>
    <div class="col-sm-4">
      <p>Skin color: {{filteredCharactersArray[itemIndex].skin_color}}</p>
    </div>
    <div class="col-sm-4">
      <p>Hair color: {{filteredCharactersArray[itemIndex].hair_color}}</p>
    </div>
    <div class="col-sm-4">
      <p>Gender: {{filteredCharactersArray[itemIndex].gender}}</p>
    </div>
    <div class="col-sm-12">
      <p>Homeworld: {{filteredCharactersArray[itemIndex].homeworld}}</p>
    </div>
  </div>
</div>
</template>

<script>

export default {
    name: 'CharacterInfo',
    data() {
      return {
        filteredCharactersArray: this.filteredArray,
        itemIndex: this.itemIndexNo,
        }
      },
      props: {
        filteredArray: Array, 
        itemIndexNo: Number,
      }
  }
</script>

<style scoped>
  .uppercase {
    text-transform: uppercase;
    margin-top: 2%;
  }
  .character-info-container {
    margin: 2% auto;
    padding: 20px;
    background: rgb(37, 37, 37);
    color: whitesmoke;
    box-shadow: 10px 5px 5px rgb(37, 37, 37);
  }
  @media(min-width: 1024px) {
    .character-info-container {
      width: 40%;
    }
  }
</style>
