<template>
 <div class="container-fluid mt-3">
    <div class="jumbotron">
      <h1 id="title"><img src="../public/flor.png" width="35"/> Trabajo Practico 4 - Josefina Sillero <img src="../public/flor.png" width="35"/></h1>
      <br>
      <Navbar />
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'

export default {
  name: 'App',
  components: {
    Navbar
  }
}
</script>

<style>
#app {
  font-family: 'Fira Sans', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#title{
  text-align: center;
  font-family: 'Fira Sans', sans-serif;
}

</style>
