<template>
  <h1>¿Quién es ese pokemon?</h1>
  <!--<div v-if="pokemonCorrecto!==null">-->
    <div v-if="pokemonCorrecto">
  <pokemon-imagen :pokemonId="pokemonCorrecto.id" :mostrarPokemon="mostrarPokemon"/>
  <pokemon-opciones :pokemons="pokemonArray" @seleccion="respuestaSeleccion($event)" />

  <div v-if="mostrarMensaje">
  <h1>{{mensajeResultado}}</h1>
  <button @click="resetJuego">Jugar de nuevo</button>
  </div>
  </div>
</template>

<script>
import PokemonOpciones from "../components/PokemonOpciones.vue"
import PokemonImagen from "../components/PokemonImagen.vue"
import obtenerPokemonOpciones from "../js/gestionarPokemon"



export default {
  name: "PaginaPokemon",
  components: {
    PokemonOpciones,
    PokemonImagen
  },

  data() {
    return {
      pokemonArray: [],
      pokemonCorrecto: null,
      mostrarPokemon: false,
      mensajeResultado: "",
      mostrarMensaje: false
    }
  },

  methods: {
    async cargarPokemonInicio() {
      this.pokemonArray = await obtenerPokemonOpciones()
      const random = Math.floor(Math.random()*4);
      this.pokemonCorrecto = this.pokemonArray[random]
      //console.log("Si cargo los nombres")
    },
    respuestaSeleccion(dato) {
      console.log("dato enviado: "+dato)
      this.mostrarPokemon=true
      if (this.pokemonCorrecto.id==dato) {
        this.mensajeResultado=`Correcto, era ${this.pokemonCorrecto.nombre}`
      } else {
        this.mensajeResultado=`Error, era ${this.pokemonCorrecto.nombre}`
      }
      this.mostrarMensaje=true
    },
    resetJuego() {
      this.pokemonArray = []
      this.mostrarPokemon = false
      this.mostrarMensaje = false
      this.cargarPokemonInicio()

    }

  },

  mounted() {
    this.cargarPokemonInicio()
  }
};
</script>

<style>
</style>