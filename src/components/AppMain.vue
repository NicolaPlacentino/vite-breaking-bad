<script>
import Card from './Card.vue';
import SelectComponent from './SelectComponent.vue';
import { store } from '../store';

export default {
    name: 'AppMain',
    components: { Card, SelectComponent },
    data() {
        return {
            store,
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
    }
}
</script>

<template>
    <div class="container">

        <!-- card section -->
        <div class="row row-cols-5 justify-content-around">
            <div class="col-auto mb-5" v-for="pokemon in store.Pokemons" :key="pokemon.number">

                <Card :pokemon="pokemon">
                </Card>

            </div>
        </div>

        <h5 class="text-center">Filtra per tipo</h5>
        <SelectComponent :pokemonTypes="this.pokemonTypes" :name="'pokemon-types'"></SelectComponent>

    </div>
</template>

<style lang="scss" scoped>

</style>