<template>
    <div class="hello">
        <h1>{{title}}</h1>
        <span v-if="is_main_series">is main series</span>
        <p>Description : {{description_en}}</p>
        <ul>
            <li v-for="(pok, index) in pokemons" :key="index">
                {{pok.pokemon_species.name}}
            </li>
        </ul>
    </div>
</template>
<script>
export default {
  name: 'HelloGame',
  props: {
    title: String,
    description: Array,
    is_main_series: Boolean,
    pokemons: Array,
  },
  data(){
    return{
      description_en: '',
    }
  },
  mounted() {
    this.description_en = this.description[3].description;
  },
}
</script>

<style scoped>
</style>