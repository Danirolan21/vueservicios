<template>
  <div class="container">
    <ul id="menu">
        <li><router-link to="/">Home</router-link></li>
        <li><router-link to="/coches">Coches</router-link></li>
        <li><router-link to="/customers">Customers</router-link></li>
        <li><router-link to="/empleados">Empleados</router-link></li>
        <li>
            Oficios
            <ul>
                <li v-for="ofi in oficios" :key="ofi">
                    <router-link :to="'/empleadosoficios/' + ofi">{{ofi}}</router-link>
                </li>
            </ul>
        </li>
    </ul>
  </div>
</template>

<script>
import ServiceEmpleados from './../services/ServiceEmpleados'

const service = new ServiceEmpleados();

    export default {
        name: "MenuComponent",
        data() {
            return {
                oficios: []
            }
        }, mounted() {
            service.getOficios().then(result => {
                this.oficios = result;
            })
        }
    }
</script>

<style>
    ul#menu, ul#menu ul {
        margin: 0;
        padding: 0;
    }
    ul#menu li {
        list-style-type: none;
        font-size: 16px;
        float: left;
        z-index: 1;
        position: relative;
        margin-left: 30px;
        transition: font-size 0.5s;
    }
    ul#menu li:hover {
        font-size: 24px;
        color: brown;
    }
    ul#menu li ul li {
        margin-left: 0;
        padding: 8px;
        width: 215px;
        border-bottom: solid 1px grey;
        margin-top: -1px;
    }
    ul#menu li ul {
        display: none;
        position: absolute;
        padding-top: 15px;
        background-color: white;
        margin-left: -8px;
    }
    ul#menu li a {
        text-decoration: none;
        color: darkslateblue;
    }
    ul#menu li:hover ul {
        display: block;
    }
    ul#menu li ul a:hover {
        color: rgb(104, 104, 104);
    }
    ul#menu ul li:hover{
        background-color: rgb(153, 153, 153);
    }
</style>