<script setup>
const name = 'Puto'
const styleColor = 'color: blue'
const arrayColores = ["blue", "red", "lima", "cean"]
const activo = true
const ArrayCarro = [{
  "color": "morado",
  "tipo": "suv",
  "capacidad": 7
},
{
  "color": "azul",
  "tipo": "suv",
  "capacidad": 7
},
{
  "color": "rojo",
  "tipo": "mini",
  "capacidad": 7
},
]

const objCarro = {
  "color": "morado",
  "tipo": "suv",
  "capacidad": 7
}

//metodos
const handleClick = (message) => {
  console.log('me diste click' + message)
}

</script>

<template>
  <h1>Hola vueJS {{ name.toUpperCase() }}</h1><br>
  <h2 :style="styleColor"> Soy Azul</h2><br>
  <h2 :style="styleColor"> {{ arrayColores[1] }}</h2><br>
  <h2 v-if="activo === true">
    activo
  </h2>
  <h2 v-else>
    Inactivo
  </h2><br>
  <h2 v-show="activo"> Big show </h2><br>
  <h2>Colores</h2><br>
  <ul>
    <li v-for="(color, index) in arrayColores" :key="index">
      {{ index }} - {{ color }}
    </li>
  </ul><br>
  <h2>Carro</h2><br>
  <ul>
    <template v-for="(auto, index) in ArrayCarro" :key="auto.tipo">
      <li v-if="auto.tipo === 'suv'">
        {{ index }} - {{ auto.color }} {{ auto.tipo }} {{ auto.capacidad }}
      </li>
    </template>
  </ul>
  <br>

  <h2>CarroObj</h2><br>
  <ul>
    <li v-for="(value, propiedad, iondex) in objCarro" :key="value">
      {{ iondex }} -- {{ propiedad }}: {{ value }}
    </li>
  </ul><br>


  <h1>Hola</h1><br>
  <button v-on:click.right="handleClick('texto 1')">Start</button>
  <button @click.left="handleClick('texto 2')">Start</button>


</template>



<style>
h1 {
  color: red
}
</style>