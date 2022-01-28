<template>
  <h2 id="puntuacion" class="position-absolute top-0 end-0">Puntuación: {{ puntos }}</h2>
  <h1>¿Quién es ese pokemon?</h1>
  <!--<div v-if="pokemonCorrecto!==null">-->
  <div v-if="pokemonCorrecto">
    <pokemon-imagen
      :pokemonId="pokemonCorrecto.id"
      :mostrarPokemon="mostrarPokemon"
    />
    <pokemon-opciones
      :pokemons="pokemonArray"
      @seleccion="respuestaSeleccion($event)"
    />

    <div v-if="mostrarMensaje">
      <h1>{{ mensajeResultado }}</h1>
      <button @click="resetJuego">Jugar de nuevo</button>
    </div>
  </div>
</template>

<script>
import PokemonOpciones from "../components/PokemonOpciones.vue";
import PokemonImagen from "../components/PokemonImagen.vue";
import obtenerPokemonOpciones from "../js/gestionarPokemon";

export default {
  name: "PaginaPokemon",
  components: {
    PokemonOpciones,
    PokemonImagen,
  },

  data() {
    return {
      pokemonArray: [],
      pokemonCorrecto: null,
      mostrarPokemon: false,
      mensajeResultado: "",
      mostrarMensaje: false,
      puntos: 0,
    };
  },

  methods: {
    async cargarPokemonInicio() {
      this.pokemonArray = await obtenerPokemonOpciones();
      const random = Math.floor(Math.random() * 4);
      this.pokemonCorrecto = this.pokemonArray[random];
      //console.log("Si cargo los nombres")
    },
    respuestaSeleccion(dato) {
      console.log("dato enviado: " + dato);
      this.mostrarPokemon = true;
      if (this.pokemonCorrecto.id == dato) {
        this.mensajeResultado = `Correcto, era ${this.pokemonCorrecto.nombre}`;
        this.puntos++;
      } else {
        this.mensajeResultado = `Error, era ${this.pokemonCorrecto.nombre}`;
        if (this.puntos > 0) {
          this.puntos--;
        }
      }
      this.mostrarMensaje = true;
    },
    resetJuego() {
      this.pokemonArray = [];
      this.mostrarPokemon = false;
      this.mostrarMensaje = false;
      this.cargarPokemonInicio();
    },
    animarPuntuacion() {},
  },

  mounted() {
    this.cargarPokemonInicio();
  },
};
</script>

<style>


#puntuacion {
  text-align: right;
  font-size: 20px;
  color: cadetblue;
}

</style>