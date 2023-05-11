<template>
    <div>
        <p>{{ character.id }}</p>
        <p>{{ character.name }}</p>
        <p>{{ character.status }}</p>
        <img :src="character.image" :alt="character.name">   
        <p>{{ character.gender }}</p>
    </div>
    
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: 'Detail',
    props: {
      id: {
        type: Number,
        required: true,
      },
    },
    data() {
      return {
        character: {},
      };
    },
    mounted() {
      axios.get(`https://rickandmortyapi.com/api/character/${this.id}`)
        .then((response) => {
          this.character = response.data;
        });
    },
  };
  </script>