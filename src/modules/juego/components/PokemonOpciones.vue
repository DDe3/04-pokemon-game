<template>
  <div class="contenedor-opciones">
    <ul>
      <li>Pokemon 1</li>
      <li>Pokemon 2</li>
      <li>Pokemon 3</li>
      <li>Pokemon 4</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "PokemonOpciones",
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