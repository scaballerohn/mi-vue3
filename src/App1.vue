<script setup>
  const vname = "Mi Vue 3 dinamico";
  const vstyleColor = "color: blue";
  const varraycolores = ["red", "green", "hn"];
  const vactivo = false;
  const varrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"]
  const varrayFrutasObj = [
    {
      name: "Manzana",
      price: "$1.00",
      description: "Una manzana",
    },
    {
      name: "Pera",
      price: "$2.00",
      description: "Una pera",
    },
    {
      name: "Naranja",
      price: "$3.00",
      description: "Una naranja",
    },
  ];

  const frutasObj = [
    {
      name: "Manzana",
      price: "$1.00",
      description: "Una manzana",
    },
  ];

const arrayFrutasStock = [
  {
    name: "Manzana",
    price: "$1.00",
    description: "Una manzana",
    stock: 0,
  },
  {
    name: "Pera",
    price: "$2.00",
    description: "Una pera",
    stock: 10,
  },
  {
    name: "Naranja",
    price: "$3.00",
    description: "Una naranja",
    stock: 0,
  },
];


</script>

<template>
  
  <h1>Hello {{vname.toUpperCase()}}</h1>
  <h2>{{ varraycolores }}</h2>
  <h2 :style="`color: ${varraycolores[1]}`"> Soy hn {{vname}}</h2>

  <h2>{{ vactivo ? "estoy activo" : "estoy inactivo" }}</h2>

  <h2 v-if="vactivo === true">Soy activo</h2>
  <h2 v-else-if = "vactivo === false"> Soy inactivo</h2>
  <h2 v-else> estoy indeciso</h2>
    
  <h1 v-show="vactivo"> Soy activoh1 </h1>
  <h1 v-show="!vactivo"> Soy inactivoh1</h1>
 
  <br>

  <!--v-for: con el in hacemos la funcion de of/in, usamos index como key por el ejemplo, siempre debemos asiganar un identificador
  unico a cada elmento de la lista 
  v-for="(fruta, index) se defina fruta como instanacion del objeto
  e index va recorrer por cada elemento-->
  <ul>  
    <li v-for="(fruta, index) in varrayFrutas" :key="index">
      {{index}} {{ fruta }}
    </li>
  </ul>

  <br>
  <!--v-for: con con objetos -->
  <ul>
    <li v-for="(fruta, index) in varrayFrutasObj" :key="fruta.name">
      <p>{{ fruta.name }}</p>
      <p>{{ fruta.price }}</p>
      <p>{{ fruta.description }}</p>
    </li>
  </ul>
  
  <br>

  <ul>
    <li v-for="(value, propieda, index) in frutasObj" :key="index">
      {{ index }} - {{ propieda}} : {{ value }}
    </li>
  </ul>
  

  <!--v-for mas v-if, un v-if tiene mayor jerarquiar q el for, por lo q vue lee
  primero el if-->
<br>

<ul>
  <template v-for = "item in arrayFrutasStock" :key="item.name">
    <li v-if="item.stock > 0">
      {{ item.name }} - {{ item.price }} - {{ item.stock }}
    </li>

    <!--v-else-if: se puede usar para definir una segunda condicion-->
    <li v-else>
      {{ item.name }} - Sin stock
    </li>

  </template>
</ul>



</template>



<style>
  h1{
    color: red; 
  }
</style>

