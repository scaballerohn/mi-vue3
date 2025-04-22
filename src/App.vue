<!-- https://bluuweb.github.io/vue-udemy/30-01-fundamentos/#v-for-v-if  -->

<script setup>
import { computed, ref } from 'vue'

const name = "Mi Vue3 Dinamico"
const contador = ref(0)
const numerosFavoritos = ref([]);


const mi_Contador = (Accion) => {
  if (Accion === 'incrementar') {contador.value++} 
  else if (Accion === 'decrementar') {    contador.value--}  
  else {contador.value = 0 } 
}

const classMiContador = computed(() => {
    if (contador.value > 0) {return 'positivo'}   
    if (contador.value < 0) {return 'negativo'}
    if (contador.value == 0) {return 'zero'}
  });

const addNumeroFavorito = (numero) => {
    numerosFavoritos.value.push(numero);  
    console.log(numerosFavoritos.value);
};

const bloquearAdd = computed(() => {
 const numero = numerosFavoritos.value.find((numero) => numero === contador.value);
  if (numero===0) {return true;}
  return numero ? true : false;
});


</script>

<!--Pracitica de Vue 3-->


<template>

  <h1>Hola {{ name.toUpperCase() }}</h1>
<br>
  <h2 :class="classMiContador"> Contador : {{contador}}</h2>
 <br>
  <button @:click="mi_Contador('incrementar')">Incrementar</button>
  <button @:click="mi_Contador('decrementar')">Decrementar</button>
  <button @:click="mi_Contador()"> Resetear Contador </button>
  <button @:click="addNumeroFavorito(contador)":disabled="bloquearAdd" > Add</button>
  <br/> 
  {{numerosFavoritos}}

<ul>
  <li v-for="(numero, index) in numerosFavoritos" :key="index">
      {{ numero }}
  </li>
    
</ul>

</template>



<style>

.positivo{
  color: green;
  font: 16px;
}
.negativo{
  color: red;
  font: 12px; 
}
.zero{
  color: blue;
  font: 12px; 
}

</style>