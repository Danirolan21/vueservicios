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
import ServiceEmpleados from './../services/ServiceEmpleados'

const service = new ServiceEmpleados();

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
                service.findEmpleado(this.idEmpleado).then(result => {
                    this.empleado = result;
                })
            }
        },
        mounted() {
            service.getEmpleados().then(result => {
                this.empleados = result;
            })
        }
    }
</script>

<style>

</style>