<template>
  <div id="app">
    <b-navbar type="dark" variant="success" class="d-flex justify-content-center">
      <b-navbar-brand href="#">Trello</b-navbar-brand>
    </b-navbar>
    
    <BoardHolder/>
  </div>
</template>

<script>
import BoardHolder from './components/BoardHolder.vue'

export default {
  name: 'app',
  components: {
    BoardHolder
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
}


</style>
