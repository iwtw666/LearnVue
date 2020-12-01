<template>
<div id="cart">
    <h1>{{msg}}</h1> 
    <input type="checkbox" @change="handleChange" v-model="checkedAll" />
    Select all
    <ul>
        <li v-for="(data, index) of datalist"
        :key="index">
        <input type="checkbox" @change="handleLiChange" v-model="cart" :value="data"/>
        {{data}}
        <button @click="data.number++">add</button>
        <button @click="handleSUB(data)">sub</button>
        </li>
    </ul>
    <p>Total price is: {{getSum()}} </p>
</div>
</template>

<script>
export default {
  name: 'Cart',
  data () {
    return {
      msg: 'Shopping Cart Demo',
      cart:[],
      datalist:[
          {
              name:"item1",
              price:10,
              number:1,
              id:"1"
          },
          {
              name:"item2",
              price:20,
              number:3,
              id:"2"
          },
          {
              name:"item3",
              price:30,
              number:2,
              id:"3"
          }
      ],
      checkedAll:false
    }
  },
  methods:{
      getSum(){
          var sum=0
          for (var i in this.cart){
              sum += this.cart[i].price*this.cart[i].number
          }
          return sum
      },
      handleChange() {
          if (this.checkedAll) {
              this.cart=this.datalist
          } else {
              this.cart = []
          }
      },
      handleLiChange() {
          if (this.cart.length === this.datalist.length) {
              this.checkedAll = true
          } else {
              this.checkedAll = false
          }
      },
      handleSUB(data) {
          var number = data.number--
          if (number === 1) {
              data.number = 1
          }
      }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#cart {
    background-color:antiquewhite;
    margin-bottom:60px;
    border:black solid 1px;
}
li {
    text-align: left;
    margin-left:38%;
}
</style>