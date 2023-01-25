<script>
import axios from 'axios';
import { store } from './store';
import AppMain from './components/AppMain.vue';
import SelectComponent from './components/SelectComponent.vue';

export default {
  name: 'App',
  components: { AppMain, SelectComponent },
  data() {
    return {
      store,
      selectedType: '',
      unfilteredUrl: 'https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons?per=10&page=1',
      pokemonTypes: [
        "Water",
        "Ground",
        "Bug",
        "Flying",
        "Psychic",
        "Grass",
        "Ice",
        "Ghost",
        "Poison",
        "Fighting",
        "Electric",
        "Rock",
        "Dark",
        "Fairy",
        "Fire",
        "Normal",
        "Dragon",
        "Steel"
      ]
    }
  },
  computed: {
    filteredUrl() {
      return `${this.unfilteredUrl}&eq[type1]=${this.selectedType}`
    }
  },
  methods: {
    getFilteredPokemons() {
      axios.get(this.filteredUrl)
        .then(res => {
          store.Pokemons = res.data.docs
        })
    },
    onOptionSelected(value) {
      this.selectedType = value
    }
  },
  created() {
    axios.get(this.unfilteredUrl)
      .then(res => {
        store.Pokemons = res.data.docs
      })
  }
}
</script>

<template>
  <h1 class="text-center my-4">Pokedex</h1>
  <AppMain></AppMain>

  <h5 class="text-center">Filtra per tipo</h5>
  <SelectComponent :pokemonTypes="this.pokemonTypes" :name="'pokemon-types'" @option-selected="onOptionSelected"
    @get-filtered-options="getFilteredPokemons">
  </SelectComponent>

</template>

<style lang="scss">
@use './assets/scss/style.scss';
</style>