<template>
  <div id="app">
    <todolist/>
    <cart/>
    <axios/>
  </div>
</template>

<script>
import todolist from './components/TodoList'
import cart from './components/Cart'
import axios from './components/Axios_watch'

export default {
  name: 'App',
  components: {
    todolist,
    cart,
    axios
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
