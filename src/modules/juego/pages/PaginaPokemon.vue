<template>
  <h1>¿Quién es ese pokemon?</h1>
  <pokemon-imagen :pokemonId="1" :mostrarPokemon="true"/>
  <pokemon-opciones />
</template>

<script>
import PokemonOpciones from "../components/PokemonOpciones.vue"
import PokemonImagen from "../components/PokemonImagen.vue"
import obtenerPokemonOpciones from "../js/gestionarPokemon"

obtenerPokemonOpciones()

export default {
  name: "PaginaPokemon",
  components: {
    PokemonOpciones,
    PokemonImagen
  },
};
</script>

<style>
</style>