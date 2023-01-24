<script>
export default {
    name: 'Card',
    props: {
        pokemon: Object,
    }
}
</script>

<template>
    <div class="my-card">
        <figure>
            <img :src="pokemon.imageUrl" :alt="pokemon.nameKebab">
        </figure>
        <span class="text-center d-block">#{{ pokemon.number }}</span>
        <h5 class="text-center fw-bold">{{ pokemon.name }}</h5>
        <div class="d-flex justify-content-around">
            <span>{{ pokemon.type1 }}</span>
            <span v-if="pokemon.type2">{{ pokemon.type2 }}</span>
        </div>
    </div>
</template>

<style lang="scss" scoped>
@use '../assets/scss/variables' as *;

.my-card {

    padding: 15px;

    background-color: $my-gray;

    border-radius: 10px;

    figure {
        background-color: white;
        border-radius: 50%;
        width: 172px;
        height: 172px;
        overflow: hidden;

        display: flex;
        justify-content: center;
        align-items: center;

        img {
            height: 80%;
            width: 80%;
        }
    }
}
</style>