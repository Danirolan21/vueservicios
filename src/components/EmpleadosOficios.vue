<template>
  <div>
    <h1>Empleados Oficios</h1>
    <table class="table table-warning">
        <thead>
            <tr>
                <th>Apellido</th>
                <th>Oficio</th>
                <th>Salario</th>
                <th>Departamento</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="emp in empleados" :key="emp">
                <td>{{emp.apellido}}</td>
                <td>{{emp.oficio}}</td>
                <td>{{emp.salario}}</td>
                <td>{{emp.departamento}}</td>
            </tr>
        </tbody>
    </table>
  </div>
</template>

<script>
import ServiceEmpleados from './../services/ServiceEmpleados'

const service = new ServiceEmpleados();

    export default {
        name: "EmpleadosOficios",
        data() {
            return {
                empleados: []
            }
        },
        methods: {
            loadEmpleados() {
                let oficio = this.$route.params.oficio;
                service.getEmpleadosOficio(oficio).then(result => {
                    this.empleados = result;
                })
            }
        }, mounted() {
            this.loadEmpleados();
        },
        watch: {
            '$route.params.oficio'(next, old) {
                if (next != old) {
                    this.loadEmpleados()
                }
            }
        }
    }
</script>

<style>

</style>