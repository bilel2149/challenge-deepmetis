<template>
  <PokimonsList :title="title" :description="description" :pokemons="pokemons" :is_main_series="is_main_series" v-if="!loading"/>
</template>

<script>
import axios from 'axios'
import PokimonsList from './components/PokimonsList.vue'

export default {
  name: 'App',
  components: {
    PokimonsList
  },
  data(){
    return{
      pokemons: [],
      title: '',
      description: '',
      is_main_series: false,
      loading: true,
    }
  },
  mounted() {
    this.getGame();
  },
  methods: {
    getGame(){
        this.loading = true;
        axios.get('https://pokeapi.co/api/v2/pokedex/2').then (data => {
            this.title = data.data.name;
            this.description = data.data.descriptions;
            this.is_main_series = data.data.is_main_series;
            this.pokemons = data.data.pokemon_entries;
            this.loading = false;
        })
        .catch ((error) => {
            console.error (error);
            this.loading = false;
        });
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
