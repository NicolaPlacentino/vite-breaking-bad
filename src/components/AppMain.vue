<script>
import Card from './Card.vue';
import { store } from '../store';

export default {
    name: 'AppMain',
    components: { Card },
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <div class="container">
        <div class="row row-cols-5 justify-content-around">
            <div class="col-auto mb-5" v-for="pokemon in store.Pokemons" :key="pokemon.number">

                <Card :pokemon="pokemon">
                </Card>

            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>

</style>