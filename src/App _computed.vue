<script setup>
import { computed, ref } from 'vue'

const name = "Mi Vue Dinamico"

const contador = ref(0)

const mi_Contador = (Accion) => {
  if (Accion === 'incrementar') {contador.value++} 
  else if (Accion === 'decrementar') {    contador.value--}  
  else {contador.value = 0 } 
}

const classMiContador = computed(() => {
  if (contador.value > 0) {
    return 'positivo'
  }   
  if (contador.value < 0) {
    return 'negativo'
  }
  if (contador.value = 0) {
    return 'zero'
  }
  });


//Metodo
const mi_handleClick = (mi_msg) => {
  console.log(mi_msg)
}

</script>

<!--Eventos  
<button v-on:click="mi_handleClick">Activame1</button>
<button @:click="mi_handleClick">Activame2</button>, abrevio con @
y puedo o no agregar () a mi envento

-Modificadores de eventos
prevent: es para quitar el comportamiento por defecto de un evento
-Reactividad REF, ej incrementar
-Propiedades computadas, pa darle color verde o rojo al contador
-->

<template>

  <h1>Hola {{ name.toUpperCase() }}</h1>
  <button v-on:click="mi_handleClick('Texto1')">Activame1</button>
  <button @:click="mi_handleClick('Texto2')">Activame2</button>
  <button @:click.mi.middle="mi_handleClick('Texto2')">Activame Rigth</button>
<br>

<h2 :class="classMiContador"> Contador : {{contador}}</h2>
 
  <button @:click="mi_Contador('incrementar')">Incrementar</button>
<br>
  <button @:click="mi_Contador('decrementar')">Decrementar</button>
<br>
  <button @:click="mi_Contador()"> Resetear Contador </button>

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
  color: black;
  font: 12px; 
}

</style>