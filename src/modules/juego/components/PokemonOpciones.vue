<template>
  <div class="contenedor-opciones">
    <ul>
      <li v-for="p in pokemons" :key="p.id" @click="$emit('seleccion', p.id)">
        {{p.nombre}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "PokemonOpciones",
  props: {
    pokemons:  {
      type: Array,
      required: true
    }
  }
};
</script>

<style>

ul {
  list-style-type: none;
}

li {
  border: 1px solid;
  border-radius: 20px;
  background-color: white;
  width: 250px;
  margin-bottom: 5px;
  cursor: pointer;
}

li:hover {
  background-color: rgba(0, 0, 0, 0.2);
}

.contenedor-opciones {
  display: flex;
  justify-content: center;
}


</style>