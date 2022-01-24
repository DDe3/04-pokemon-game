<template>
  <h1>¿Quién es este pokemon?</h1>
  <!-- Componente Imagen -->
  <pokemon-imagen/>
  <!-- Componente Opciones -->
  <pokemon-opciones/>
</template>

<script>
import PokemonImagen from "../components/PokemonImagen.vue"
import PokemonOpciones from "../components/PokemonOpciones.vue"


export default {
  name: "PaginaPokemon",
  components: {
    PokemonImagen,
    PokemonOpciones
  },
};
</script>

<style>
</style>