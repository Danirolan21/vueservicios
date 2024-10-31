<template>
  <div>
    <CustomersComponent/>
    <!-- <CochesComponent/> -->
  </div>
</template>

<script>
import CustomersComponent from './components/CustomersComponent.vue'
// import CochesComponent from './components/CochesComponent.vue'

export default {
  name: 'App',
  components: {
    CustomersComponent
    // CochesComponent
  }
}
</script>

<style>
body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  --color: #E1E1E1;
  background-color: #F3F3F3;
  background-image: linear-gradient(0deg, transparent 24%, var(--color) 25%, var(--color) 26%, transparent 27%,transparent 74%, var(--color) 75%, var(--color) 76%, transparent 77%,transparent),
      linear-gradient(90deg, transparent 24%, var(--color) 25%, var(--color) 26%, transparent 27%,transparent 74%, var(--color) 75%, var(--color) 76%, transparent 77%,transparent);
  background-size: 55px 55px;
}
.row {
  display: flex;
  flex-wrap: wrap;
  gap: 15px;
}
.justify-content-space-between {
  justify-content: space-around;
}
.container {
  width: 90%;
  margin: 0 auto;
}
</style>
