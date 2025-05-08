<script setup lang="ts">
const { data: pokemons } = await useFetch('https://pokeapi.co/api/v2/pokemon?offset=252&limit=135')
</script>

<template>
  <div>
    <h1>Pokemon</h1>
    <ul>
        <li v-for="pokemon in pokemons.results" :key="pokemon.id">
            {{ pokemon.name }}
        </li>
    </ul>
  </div>
</template>

<style scoped>
li {
    display: flex;
    align-items: center;
}
</style>

