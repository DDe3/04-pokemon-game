<template>
  <img :src=cargarImagen alt="Not found"/>
</template>

<script>
import { computed } from "@vue/runtime-core";
export default {
  name: "PokemonImagen",

  data() {
    return {
    };
  },
  computed: {
    cargarImagen() {
      return "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/1.svg";
    },
  },
};
</script>


<style>
</style>