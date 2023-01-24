<script>
import axios from 'axios';
import { store } from './store';
import AppMain from './components/AppMain.vue';
export default {
  name: 'App',
  components: { AppMain },
  data() {
    return {
      store
    }
  },
  created() {
    axios.get('https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons?per=10&page=1')
      .then(res => {
        store.Pokemons = res.data.docs
      })
  }
}
</script>

<template>
  <h1 class="text-center my-4">Pokedex</h1>
  <AppMain></AppMain>
</template>

<style lang="scss">
@use './assets/scss/style.scss';
</style>