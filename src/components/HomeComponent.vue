<template>
  <div>
    <h1>Home</h1>
    <h2 style="color: red">
        {{mensaje}}
    </h2>
  </div>
</template>

<script>
import ServiceEjemplo from './../services/ServiceEjemplo'
//PARA PODER UTILIZAR EL SERVICIO NECESITAMOSUNA CONSTANTE
//INSTANCIADA CON LA CLASE DEL SERVICIO NECESARIO
const service = new ServiceEjemplo();

    export default {
        name: "HomeComponent",
        data() {
            return {
                mensaje: ""
            }
        },
        mounted() {
            this.mensaje = service.getSaludo("Alumno");
        }
    }
</script>

<style>

</style>