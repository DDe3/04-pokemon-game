<template>
  <div class="contenedor-imagen">
    <img :src="cargarImagen" alt="Not found" class="ocultar-pokemon" />
    <img :src="cargarImagen" alt="Not found" v-if="mostrarPokemon" />
  </div>
</template>

<script>
import { computed } from "@vue/runtime-core";
export default {
  name: "PokemonImagen",

  props: {
    pokemonId: {
      type: Number,
      required: true,
    },
    mostrarPokemon: {
      type: Boolean,
      required: true,
    }
  },

  computed: {
    cargarImagen() {
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`;
    },
  },
};
</script>


<style>
.ocultar-pokemon {
  filter: brightness(0);
}

img {
  height: 200px;
  position: absolute;
  right: 40%;
}

.contenedor-imagen {
  height: 200px;
}
</style>