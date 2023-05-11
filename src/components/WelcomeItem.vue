

<template>  
  <div>
    <h1>Rick and Morty Characters</h1>
    <ul>
      
      <li v-for="character in characters" :key="character.id">
        <router-link :to="'/character/' + character.id">
          {{ character.name }}
        </router-link>
         
         
      </li>
     
    </ul>
  </div>
    
</template>

<style > 
</style>
<script>
import axios from 'axios';



export default {
  name: 'CharacterList',
  data() {
    return {
      characters: [],
    };
  },

 


  mounted() {
    axios.get('https://rickandmortyapi.com/api/character')
      .then((response) => {
        this.characters = response.data.results;
      });
  },
};
</script>