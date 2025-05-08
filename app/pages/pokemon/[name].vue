<script setup lang="ts">
const route = useRoute()
const { data: pokemon } = await useFetch(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)
</script>

<template>
  <div class="container mx-auto p-4">
    <div v-if="pokemon" class="max-w-2xl mx-auto">
      <h1 class="text-3xl font-bold mb-4 capitalize">{{ pokemon.name }}</h1>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <img :src="pokemon.sprites.front_default" :alt="pokemon.name" class="w-64 h-64 mx-auto" />
        <div>
          <h2 class="text-xl font-semibold mb-2">Detalles</h2>
          <p><strong>Altura:</strong> {{ pokemon.height / 10 }}m</p>
          <p><strong>Peso:</strong> {{ pokemon.weight / 10 }}kg</p>
          <div class="mt-4">
            <h3 class="text-lg font-semibold mb-2">Tipos:</h3>
            <div class="flex gap-2">
              <span v-for="type in pokemon.types" :key="type.type.name"
                class="px-3 py-1 rounded-full bg-gray-200 capitalize">
                {{ type.type.name }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template> 