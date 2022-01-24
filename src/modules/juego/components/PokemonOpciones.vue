<template>
  <img :src="enlace" alt="Not found" />
  <div class="contenedor-opciones">
    <input type="text" placeholder="Ingrese un ID de Pokemon" v-model="nid" />
    <button @click="consultarPokemon">Consultar</button>
  </div>
</template>

<script>
export default {
  name: "PokemonOpciones",
  //"https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/1.svg"

  props: {
    url: {
      type: String,
      default: null,
    },
    id: {
      type: Number,
      default: null,
    },
  },

  data() {
    return {
      enlace: this.url,
      nid: this.id
    }
  },

  computed: {
    consultarPokemon() {
      console.log("Este es el id: " + this.id);
      this.enlace =
        "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/" +
        this.nid +
        ".svg";
    },
  },
};
</script>

<style>
button {
  cursor: pointer;
  background-color: rgba(0, 0, 0, 0.2);
}

input,
button {
  margin-right: 5px;
  border-radius: 5px;
}

button:hover {
  background-color: aqua;
}

.contenedor-opciones {
  display: flex;
  justify-content: center;
}

img {
  margin: 20px;
}
</style>