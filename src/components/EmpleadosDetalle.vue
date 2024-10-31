<template>
  <div class="container">
    <h1>Empleados Detalles</h1>
    <form v-on:submit.prevent="buscarEmpleado()">
        <label class="form-label">Seleccione empleado:</label>
        <select class="form-select" v-model="idEmpleado">
            <option v-for="empleado in empleados" :key="empleado" :value="empleado.idEmpleado">
                {{empleado.apellido}}
            </option>
        </select>
        <button class="btn btn-info mt-3">
            Detalles Empleado
        </button>
    </form>
    <hr v-if="empleado" class="border border-primary border-3 opacity-75"/>
    <div v-if="empleado">
        <dl>
            <dt>Oficio: </dt>
            <dl>{{empleado.oficio}}</dl>
            <dt>Salario: </dt>
            <dl>{{empleado.salario}}</dl>
            <dt>Departamento: </dt>
            <dl>{{empleado.departamento}}</dl>
        </dl>
    </div>
  </div>
</template>

<script>
import Global from '@/Global'
import axios from 'axios'

    export default {
        name: "EmpleadosDetalle",
        data() {
            return {
                empleados: [],
                idEmpleado: 0,
                empleado: null
            }
        },
        methods: {
            buscarEmpleado() {
                let request = "api/empleados/" + this.idEmpleado;

                let url = Global.urlApiEmpleados + request;
                axios.get(url).then( response => {
                    console.log("Leyendo Empleado Por Id...");                
                    this.empleado = response.data;
                })
            }
        },
        mounted() {
            let request = "api/empleados";

            let url = Global.urlApiEmpleados + request;
            axios.get(url).then( response => {
                console.log("Leyendo Empleados...");                
                this.empleados = response.data;
            })
        }
    }
</script>

<style>

</style>