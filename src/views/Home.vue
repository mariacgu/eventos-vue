<template>
  <header>
<h1> {{titulo}}</h1>
</header>
<main>
<div>
<h2>Registrar Reserva</h2>
<form id="formulario_reserva" action="#" method="post">
<label for ="cliente">Nombre del Usuario</label>
<input type="text" name="cliente" v-model="reserva.cliente">
<label for ="documento">Documento</label>
<input type="text" name="documento">
<label  for ="Tipo de paquete">tipo de Paquete</label>
<div>
<input v-if="tipop" type="radio" name="tipo_paquete" value="0">
<input v-if="tipop" type="radio" name="tipo_paquete" value="1">
</div>
<label for ="transporte">Incluir trasporte al punto de partida</label>
<input v-if="transporte_si" type="checkbox" name="transporte_si" value="Si">
<label for="num_transporte">Cantidad de transporte</label>
<input type="number" name="num_transporte">
<label v-if="personas" for="num_personas">N. Personas</label>
<input type="number" name="num_personas">
<button type="reset">Limpiar</button>
<button onclick="procesarInformation()" type="summit">Enviar</button>
</form>
<h2>Cliente:{{reserva.cliente}}</h2>
</div>
<div>
<h2>Listado de Paquetes</h2>

<table>
<thead>
 <th>Sierra Nevada</th>
 <th>Cocora</th>
</thead>
<tbody id="datos_reserva">
  <tr v-for="unReserva in listaReservas" :key="unReserva">
      <td>{{unReserva.cliente}}</td>
      <td>{{unReserva.documento}}</td>
      <td>{{unReserva.tipo_paquete}}</td>
    </tr>

</tbody>
</table>
</div>
</main>
<!--<script src="js/reservas.js"></script>  -->
</template>

<script>
// @ is an alias to /src

import HelloWorld from '@/components/HelloWorld.vue'
export default {

  data(){
    return {
      titulo:"Gestion de Reservas",
      listaReservas:[
        {cliente:"Maria Clara",
        documento:"12345",
        tipo_paquete:1
        },
        {cliente:"Laura",
        documento:"67890",
        tipo_paquete:2
        },
        {cliente:"David",
        documento:"11111",
        tipo_paquete:1
        },
      ],
      reserva:{
        cliente:"",
        documento:"",
        tipo_paquete:{},
        
      },
      tipo_paquete:0,
      extra:false,
      tipop:false,
      personas:0,
      transporte_si:false,

    };
  },
  name: 'Home',
  components: {
    HelloWorld
  }
}
</script>

<style scoped>
body{
 padding: 2tem;
}

#formulario_reserva{
 display: grid;
 grid-template-columns: 5rem 10rem;
 row-gap: 1rem;
 column-gap:0.5rem;
}
</style>
