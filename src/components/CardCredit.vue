<template>
  <div id="containerCard" class="containerCard">
      
      <form>    <!--Se crea formulario en la página-->
        <div>
          <label>Título de la tarjeta: </label>
          <input v-model="tarjeta.tituloTarjeta" /> <!--Crea un campo de entrada en el formulario v-model=tarjeta.tituloTarjeta esta vinculado a una variable tarjeta en el modelo de datos de Vue.js-->
        </div>
        <!---->
        <div>
          <label for="imagen">Chip SRC:</label>
      <select name="imagen" id="imagen" v-model="tarjeta.imagenSeleccionChip"><!--Crea un menu desplegable en el formulario y v-model=tarjeta.imagenSeleccionChip , esta vinculado a una variable tarjeta en el modelo de datos de Vue.js-->
        <option disabled value="">Elige el chip a usar</option><!--Define una opción en un menú desplegable y se utiliza dentro de un ciclo v-for para mostrar dinámicamente las opciones.-->
        <option v-for="imagen in tarjeta.imagenesChip" 
        :key="imagen.id" :value="imagen.path">{{ imagen.texto }}</option><!--Se utiliza para asignar una clave única a cada opción en el menú desplegable.-->
      </select>     <!--Determina el valor seleccionado cuando se elige una opción en el menú desplegable-->
        </div>
        <!----->
        <div>
          <label>Número: </label> <!--Crea un campo de entrada en el formulario , vinculado a la variable tarjeta.numero en el modelo de datos Vue.js-->
          <input v-model="tarjeta.numero" />
        </div>

        <div>
          <label>Fecha de expiración: </label>  <!--Crea otro campo de entrada en el formulario, vinculado a la variable tarjeta.fecha.DeExpiracion en el modelo de datos de Vue.js-->
          <input v-model="tarjeta.fechaDeExpiracion" />
        </div>

        <div>
          <label>Propietario: </label> <!--Se crea otro campo de entrada a formulario, vinculado a otra variable.-->
          <input v-model="tarjeta.propietario" />
        </div>

        <div>
          <label for="imagenBrand">Tipo de tarjeta SRC:</label>
      <select name="imagenBrand" id="imagenBrand" v-model="tarjeta.imagenSeleccionBrand"> <!--Crea otro menú desplegalbe en el formulario, muestra opciones dinámicas con las img de la marca de tarjeta-->
        <option disabled value="">Elige la marca de tu tarjeta</option>
        <option v-for="imagen in tarjeta.imagenesBrand" 
        :key="imagen.id" :value="imagen.path">{{ imagen.texto }}</option>
      </select>
        </div>
      </form>
    
 

      <div class="tarjeta"> <!-- Se crea una tarjeta con la clase tarjeta y se muestra la info ingresada en la tarjeta a medida que se completa el formulario -->
        <h3>{{ tarjeta.tituloTarjeta }}</h3><!--Se utilizan las llaves para interpolar y mostrar dinámicamente el contenido de las propiedades de tarjeta  en la página-->
        <img width="40" :src="tarjeta.imagenSeleccionChip" :alt="tarjeta.infoChip" />
        <div>
          <h2>{{ tarjeta.numero }}</h2>
          <span>Fecha Exp: <b>{{ tarjeta.fechaDeExpiracion }}</b></span>
        </div>
        <footer>
          <span>{{ tarjeta.propietario }}</span>
          <img :src="tarjeta.imagenSeleccionBrand" width="60" />
        </footer>
      </div>
  </div>
</template>

<script>  /*Define un componente CreditsCard que exporta un objeto con algunas propiedades, el objeto tiene la propiedad name con el valor CreditsCard y la propiedad data , que es una función que devuelve un objeto con varias propiedades. */
export default {
name: 'CreditsCard',
data(){   /*Dentro del objeto retornado por la función data, encontramos la propiedad tarjeta que es un objeto con varias propiedades y la mayoría son una cadena vacía, salvo img de chip y img de tarjeta. */
  return{
      tarjeta: {
          tituloTarjeta: "",
          numero: "",
          imagenSeleccionChip: "",
          infoChip: "Imagen chip",
          imagenesChip: [
        {id: 1, path: "/img/chip.png", texto: "Chip Visa - Mastercard - Diners Club"},
        /*{id: 2, path: "/img/chip2.png", texto: "chip "},*/
        {id: 3, path: "/img/chip3.png", texto: "Chip Master Plop"},
    ],
    fechaDeExpiracion: "",
    propietario: "",
    imagenSeleccionBrand: "",
    imagenesBrand: [
        {id: 1, path: "/img/visa.png", texto: "Visa"},
        {id: 2, path: "/img/masterCard.png", texto: "Mastercard"},
        {id: 3, path: "/img/dinersClub.png", texto: "Diners Club"},
        {id: 4, path: "/img/plop2.png", texto: "Master Plop"},
        
    ],
      }
  }
}

}/*Estas propiedades son utilizadas para almacenar la información de una tarjeta de crédito, incluyendo varios campos e img  de chip y marcas  de las tarjetas cargadas desde rutas locales en la aplicación. */
</script>

<style scoped>/*Estilos */
* {
margin: 0;
}
.containerCard {
  background: linear-gradient(rgb(13, 58, 208), rgb(161, 234, 241));  
  border-radius: 15px;
  box-shadow: 0px 0px 10px 2px black;
display: flex;
justify-content: space-around;
align-items: center;
height: 60vh;
font-size: 10px;
font-family: sans-serif;
gap: 40px;
}


form {
  background: linear-gradient(rgb(186, 139, 182), rgb(217, 127, 127));
padding: 18px;
border-radius: 20px;
border: ridge 1px;
box-shadow: 0px 0px 10px 2px black;
font-weight: bold;
display: flex;
flex-direction: column;
gap: 15px;
justify-content: center;
}
form div {
display: grid;
grid-template-columns: 100px 200px;
align-items: center;
gap: 5px;
}

form div label {
text-align: right;
}

.tarjeta {
width: 400px;
height: 230px;
background: linear-gradient(rgba(187, 132, 187, 0.9), 0.849), rgb(232, 149, 224));
color: rgb(0, 0, 0);
border-radius: 20px;
padding: 20px;
box-shadow: 0px 0px 10px 2px black;
display: flex;
flex-direction: column;
justify-content: space-between;
}

h3 {
font-size: 20px;
}

h2 {
font-size: 30px;
letter-spacing: 10px;
margin-bottom: 15px;
text-shadow: 0px 0px 1px gold;
font-family: Times;
}

b {
font-size: 16px;
}

footer {
display: flex;
justify-content: space-between;
align-items: flex-end;
font-weight: bold;
font-size: 18px;
text-transform: uppercase;
font-style: italic;
}
</style>