<template>
  <div id="app">
    <todolist/>
    <cart/>
  </div>
</template>

<script>
import todolist from './components/TodoList'
import cart from './components/Cart'

export default {
  name: 'App',
  components: {
    todolist,
    cart
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
