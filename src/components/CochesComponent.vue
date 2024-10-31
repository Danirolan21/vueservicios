<template>
    <div>
        <h1>Servicios Api Coches</h1>
        <div v-if="!status" class="terminal-loader">
            <div class="terminal-header">
                <div class="terminal-title">Status</div>
                <div class="terminal-controls">
                    <div class="control close"></div>
                    <div class="control minimize"></div>
                    <div class="control maximize"></div>
                </div>
            </div>
            <div class="text">Loading...</div>
        </div>
        <table v-else border="1">
            <thead>
                <tr>
                    <th>Marca</th>
                    <th>Modelo</th>
                    <th>Conductor</th>
                    <th>Imagen</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="car in coches" :key="car">
                    <td>
                        {{car.marca}}
                    </td>
                    <td>
                        {{car.modelo}}
                    </td>
                    <td>
                        {{car.conductor}}
                    </td>
                    <td>
                        <img style="width: 150px" :src="car.imagen" alt="Imagen Coche">
                    </td>
                </tr>   
            </tbody>
        </table>
    </div>
</template>

<script>
    import axios from 'axios';
    import Global from './../Global'
    //SI NECESITAMOS VARIABLES DECLARADAS PARA UTILIZAR EN LOS
    //METODOS (mounted, created, methods) LAS DECLARAMOS AQUI
    // let urlApiCoches = "https://apicochespaco.azurewebsites.net/";

    export default {
        name: "CochesComponent",
        data() {
            return {
                coches: [],
                status: false
            }
        },
        mounted() {
            let request = "/webresources/coches";

            //LAS VARIABLES DECLARADAS POR ENCIMA DE export default
            //NO UTILIZAN LA PALABRA this
            let url = Global.urlApiCoches + request;
            axios.get(url).then(response => {
                console.log("Leyendo servicio..");
                this.coches = response.data;
                this.status = true
            })
        }
    }
</script>

<style scoped>
@keyframes blinkCursor {
  50% {
    border-right-color: transparent;
  }
}

@keyframes typeAndDelete {
  0%,
  10% {
    width: 0;
  }
  45%,
  55% {
    width: 6.2em;
  } /* adjust width based on content */
  90%,
  100% {
    width: 0;
  }
}

.terminal-loader {
  border: 0.1em solid #333;
  background-color: #1a1a1a;
  color: #0f0;
  font-family: "Courier New", Courier, monospace;
  font-size: 1em;
  padding: 1.5em 1em;
  width: 12em;
  margin: 100px auto;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  border-radius: 4px;
  position: relative;
  overflow: hidden;
  box-sizing: border-box;
}

.terminal-header {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1.5em;
  background-color: #333;
  border-top-left-radius: 4px;
  border-top-right-radius: 4px;
  padding: 0 0.4em;
  box-sizing: border-box;
}

.terminal-controls {
  float: right;
}

.control {
  display: inline-block;
  width: 0.6em;
  height: 0.6em;
  margin-left: 0.4em;
  border-radius: 50%;
  background-color: #777;
}

.control.close {
  background-color: #e33;
}

.control.minimize {
  background-color: #ee0;
}

.control.maximize {
  background-color: #0b0;
}

.terminal-title {
  float: left;
  line-height: 1.5em;
  color: #eee;
}

.text {
  display: inline-block;
  white-space: nowrap;
  overflow: hidden;
  border-right: 0.2em solid green; /* Cursor */
  animation: typeAndDelete 4s steps(11) infinite,
    blinkCursor 0.5s step-end infinite alternate;
  margin-top: 1.5em;
}
</style>