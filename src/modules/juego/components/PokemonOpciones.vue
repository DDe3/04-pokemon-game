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
li {
  border: 1px solid;
  border-radius: 20px;
  background-color: white;
  width: 250px;
  margin-bottom: 5px;
  cursor: pointer;
}

li:hover {
  background-color: rgba(0, 0, 0, 0.1);
}

ul {
  list-style-type: none;
}

.contenedor-opciones {
    display: flex;
    justify-content: center;
}

</style>