<template>
<div id="axios">
    <h1>{{msg}}</h1>
    Ask a yes/no question: 
    <input v-model="question">
    <p> {{answer}} </p>
</div>

</template>


<script>
export default {
  name: 'Axios',
  data () {
    return {
      msg: 'Axios Demo',
      question:"",
      answer: 'I cannot give you an answer until you ask a question!'
    }
  },
  watch: {
      question(newq, oldq){
          this.answer = 'Waiting for you to stop typing...'
          this.Debounce()
          }
    },
  created: function(){
      this.Debounce = _.debounce(this.getAnswer,500)
    },
  
  methods:{
      getAnswer() {
          if (this.question.indexOf('?') === -1) {
              this.answer="Questions usually contain a question mark. ;-)"
              return
          }
          this.answer="Thinking......"
          var vm = this
          axios.get('https://yesno.wtf/api').then(function(response){
              vm.answer=_.capitalize(response.data.answer)
          })
          .catch(function(error) {
              vm.answer = 'Error! Could not reach the API. ' + error
          })
      }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#axios {
    background-color:azure;
    margin-bottom:60px;
    border:black 1px solid;
}
li {
    text-align: left;
    margin-left:42%;
}
</style>