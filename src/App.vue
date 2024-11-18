<template>

<Navbar></Navbar>

<h1>APP . VUE LINK PR</h1>

  <router-view/>

</template>

<script>
import Navbar from './components/Navbar.vue';

  export default{
    components: { Navbar }

  }

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 600px;
  margin: 0 auto;
  text-align: center;
  color: #2c3e50;
}


</style>