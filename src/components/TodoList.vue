<template>
<div id="todolist">
    <h1>{{msg}}</h1>
    <input v-model="input">
    <button @click="addItem">Add thing</button>
    <h3 v-show="added">(click the item to remove it)</h3>
    <ul>
        <li v-for="(item, index) of list"
        :key="index"
        :index="index"
        @click="remove(index)">
        {{item}}
        </li>
    </ul>
</div>
</template>

<script>
export default {
  name: 'TodoList',
  data () {
    return {
      msg: 'Todolist Demo',
      input:"",
      list:[],
      index:"",
      added:false
    }
  },
  methods:{
      addItem() {
          this.list.push(this.input)
          this.input=""
          this.added=true
      },
      remove(index) {
          this.list.splice(index,1)
          if (this.list.length===0) {
              this.added=false
          }
      }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#todolist {
    background-color: aliceblue;
    margin-bottom:60px;
    border:black 1px solid;
}
li {
    text-align: left;
    margin-left:42%;
}
</style>