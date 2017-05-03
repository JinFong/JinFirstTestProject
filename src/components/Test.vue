<template>
  <div class="test">
    <a v-bind:href="blogUrl">Vist my blog</a>
    <h1>{{user.fullName.split(' ')[0]}}</h1>
    <p v-if = "itemsInStock > 10">{{itemsInStock}} in  Stock.</P>
    <p v-else-if = "itemsInStock > 0">Hurry up, there are just a few items left!</P>
    <p v-else>too bad, we're all out!</p>
    <P> Movie Title = {{movieTitle}}</p>
    <p> Release Year = {{releaseYear}}</p>
    <p> The Movie is {{isMovieOld(releaseYear) ? 'old' : 'new'}}</p>
    <div v-bind:title="movieTitle">Hover your mouse here to see movie title!</div>
    <h1>Employees</h1>
    <thead>
      <tr>
        <th>Name</th>
        <th>Title</th>
        <th>Company</th>
        <th>Index</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for ="(employee, index) in employees"></tr>
      <tr v-for ="employee in employees">
        <td>{{employee.name}}</td>
        <td>{{employee.title}}</td>
        <td>{{company}}</td>
      </tr>
    </tbody>
  </div>
</template>

<script>
  export default {
    name: 'test',
    data() {
      return {
        blogUrl: 'http://codingexplained.com',
        movieTitle: 'The matrix',
        releaseYear: 1999,
        itemsInStock: 0,
        company: 'VueX Ltd.',
        showName: true,
        user: {
          firstName: 'John',
          lastName: 'Smith',
          fullName: 'John Smith',
          age: 27
        },
        employees:[
          {name: 'Abby', title: 'accountant'},
          {name: 'Brandon', title: 'manager'},
          {name: 'Mary', title: 'IT'}
        ]
      }
    },
    methods: {
      isMovieOld: function (releaseYear){
        return releaseYear < 2000;
      }
    },
    computed: {
      getFullName: function() {
        return this.user.firstName + ' '+ this.user.lastName;
      }
    }
}
</script>

<style scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
