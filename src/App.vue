<template>
  <div id="app">
    <BackgroundSlide/>
  </div>
</template>

<script>
import BackgroundSlide from './components/BackgroundSlide'

export default {
  name: 'app',
  components: {
    BackgroundSlide
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


</style>
