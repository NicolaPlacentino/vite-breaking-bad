<script>
export default {
    name: 'SelectComponent',
    props: {
        pokemonTypes: Array,
        name: String,
    }
}
</script>

<template>
    <select :name="name" id="" class="form-select">
        <option selected value="">-</option>
        <option v-for="pokemonType in this.pokemonTypes" :value="pokemonType">{{ pokemonType }}</option>
    </select>
</template>

<style lang="scss" scoped>
@use '../assets/scss/variables' as *;

select {
    width: 50%;
    margin: 0 auto;
    margin-bottom: 50px;
}
</style>