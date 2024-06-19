<template>
  <div id="app">
<img width="180" src="masterplop.png" alt="" /> 
<h1>Formulario de Tarjeta de Crédito</h1>

<CreditsCard />
    
  </div>
</template>

<script>/*Se importa componente CreditsCard desde archivo CardCredit.vue y se establece como un componente en el objeto exportado */
import CreditsCard from './components/CardCredit.vue'
export default {
  name: 'App',
  components: {        /*Dentro de la propiedad components, se incluye el componente CreditsCard */
    CreditsCard
    
  }
}
</script>

<style>  /*Se establece un estilo de fondo para el cuerpo de la pàgina y se centra el texto del elemento h1. */
body{
  background: linear-gradient(rgb(174, 117, 165), rgb(218, 113, 113));
}
h1{
  text-align: center;
}
</style>
