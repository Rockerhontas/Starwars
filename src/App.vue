<template>
  <div id="app">

    <Header /> 
    <Charas />

  </div>

</template>

<script>
import Header from './components/Header'
import Charas from './components/Charas.vue'

export default {
  name: 'app',
  components: {
    Charas,
    Header
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Montserrat|Orbitron&display=swap');

body {
  background: url(./assets/blackbg.png);
  font-family: 'Montserrat', sans-serif;
  text-align: center;
  color: #c0c0c0;
  margin-top: 60px;
  line-height: 1.4;
  font-size: 1.1em;
}
</style>