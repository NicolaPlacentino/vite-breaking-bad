<script>
export default {
    name: 'SelectComponent',
    data() {
        return {
            selectedOption: ''
        }
    },
    props: {
        pokemonTypes: Array,
        name: String,
    },
    emits: ['option-selected', 'get-filtered-options']
}
</script>

<template>
    <div class="d-flex">
        <select :name="name" v-model="selectedOption" @change="$emit('option-selected', selectedOption)" id="select"
            class="form-select">
            <option selected value="">-</option>
            <option v-for="pokemonType in this.pokemonTypes" :value="pokemonType">{{ pokemonType }}</option>
        </select>
        <button @click="$emit('get-filtered-options')" class="btn btn-primary ms-3">Cerca</button>
    </div>
</template>

<style lang="scss" scoped>
@use '../assets/scss/variables' as *;

div {
    width: 50%;
    margin: 0 auto;
    margin-bottom: 50px;

    select {
        display: inline;
    }
}
</style>