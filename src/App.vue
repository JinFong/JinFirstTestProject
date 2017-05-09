<template>
  <div id="app">
    <test></test>


  </div>
</template>

<script>
import Test from './components/Test.vue'

export default {
  name: 'app',
  components:{
    Test
  },
  data(){
    return {
      persons:[
        { id: 1, name: 'Andy'},
        { id: 2, name: 'Brandon'},
        { id: 3, name: 'Mary'}
      ]
    }
  },
  methods:{
    AddNewPerson: function(){
      var highestId = Math.max.apply(Math, this.persons.map(function(p){
        return p.id;
      }));
      var names = ['Billy','Michael','Steve','Diane','Peter'];

      this.persons.push({
        id: highestId + 1,
        name: names[Math.floor(Math.random() * name.length)]
      });
    },
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
