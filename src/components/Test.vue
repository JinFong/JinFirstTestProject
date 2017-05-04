<template>
  <div class="test">
    <a v-bind:href="blogUrl">Vist my blog</a>
    </br>
    <a href="http://google.com" v-on:click ="showDialog" target ="_blank">click here!</a>
    <h1>{{user.fullName.split(' ')[0]}}</h1>

    <p>{{ user.counter }}</p>
    <p>{{ getFullName }}</p>
    <button v-on:click = "user.counter++">Increase Counter</button>
    <button v-on:click = "changeName">Change Name</button>
    </br>
    </br>
    <input type = "text" v-on:keyup.enter ="pressedEnter">
    <p v-if = "itemsInStock > 10">{{itemsInStock}} in  Stock.</P>
    <p v-else-if = "itemsInStock > 0">Hurry up, there are just a few items left!</P>
    <p v-else>too bad, we're all out!</p>
    <P> Movie Title = {{movieTitle}}</p>
    <p> Release Year = {{releaseYear}}</p>
    <p> The Movie is {{isMovieOld(releaseYear) ? 'old' : 'new'}}</p>
    <div v-bind:title="movieTitle">Hover your mouse here to see movie title!</div>
    <h1>Moives</h1>
    <ul>
      <li v-for = "title in movieTitles">{{title}}</li>
    </ul>
    <h1>Employees</h1>
    <table border="1">
    <thead>
      <tr>
        <th>Name</th>
        <th>Title</th>
        <th>Company</th>
        <th>Index</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for ="employee in employees">
        <td>{{employee.name}}</td>
        <td>{{employee.title}}</td>
        <td>{{company}}</td>
      </tr>
    </tbody>
    </table>
  </div>
</template>

<script>
  export default {
    name: 'test',
    data() {
      return {
        blogUrl: 'http://codingexplained.com',
        movieTitle: 'The matrix',
        movieTitles: ['The matrix', 'The matrix reload','The matrix revolutions'],
        releaseYear: 1999,
        itemsInStock: 0,
        company: 'VueX Ltd.',
        showName: true,
        user: {
          counter: 1,
          firstName: 'John',
          lastName: 'Smith',
          fullName: 'John Smith',
          age: 27
        },
        employees:[
          {name: 'Abby', title: 'accountant'},
          {name: 'Brandon', title: 'manager'},
          {name: 'Mary', title: 'IT'}
        ],
      }
    },
    methods: {
      isMovieOld: function (releaseYear){
        return releaseYear < 2000;
      },
      showDialog: function(){
        alert("hello world");
      },
      pressedEnter: function(){
        alert("You pressed the Enter Key!");
      },
      changeName: function(){
        this.user.firstName = 'Mark',
        this.user.lastName = 'Gondale'
      },
    },
    computed: {
      getFullName: function() {
        return this.user.firstName + ' '+ this.user.lastName;
      }
    }
}
</script>

<style scoped>

</style>
