<template>
  <div class="test">
    <a v-bind:href="blogUrl">Vist my blog</a>
    </br>
    <a href="http://google.com" v-on:click ="showDialog" target ="_blank">click here!</a>

    <p>{{ message | uppercase(false)}}</p>
    <p>{{ message | uppercase(true) | removeSpaces}}</p>

    <p>{{user.fullName.split(' ')[0]}}</p>
    <p>{{ user.counter }}</p>
    <p>{{ getFullName }}</p>
    <button v-on:click = "user.counter++">Increase Counter</button>
    <button v-on:click = "changeName">Change Name</button>
    </br>
    </br>
    <input type = "text" v-on:keyup.enter ="pressedEnter">

    <hr>
    <h1>Moives</h1>
    <ul>
      <li v-for = "title in movieTitles">{{title}}</li>
    </ul>
    <ol>
      <li v-for = "movie in formattedMovies">{{movie}}</li>
    </ol>
    <button v-on:click = "addMovie">Add Movie</button>

    <p v-if = "itemsInStock > 10">{{itemsInStock}} in  Stock.</P>
    <p v-else-if = "itemsInStock > 0">Hurry up, there are just a few items left!</P>
    <p v-else>too bad, we're all out!</p>
    <P> Movie Title = {{movieTitle}}</p>
    <p> Release Year = {{releaseYear}}</p>
    <p> The Movie is {{isMovieOld(releaseYear) ? 'old' : 'new'}}</p>
    <div v-bind:title="movieTitle">Hover your mouse here to see movie title!</div>

    <hr>
    <h1>Employees</h1>
    <div v-for = "(index, employee) in employees">{{employee}} : {{index}}
    </div>
    </br>
    <table border="1">
    <thead>
      <tr>
        <th>Name</th>
        <th>Title</th>
        <th>Company</th>
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

    <hr>
    <div v-bind:style="{'margin':'100px 100px','transform':'rotate(3deg)','box-shadow':'0 20px 30px rgba(0,0,0,1)','background-color':'red'}"> CSS Style Testing
    </div>

    <div class = "static" v-bind:class="{ 'class-a':isA, 'class-b':isB}">This is CSS Test
      <div align = "center">
        <button @click = "isA = !isA">isA = {{isA}}</button>
        <button @click = "isB = !isB">isB = {{isB}}</button>
      </div>
    </div>
    </br>
    </br>

    <hr>
    <ol>
      <li v-for = "item in items">{{item.msg}}</li>
    </ol>
    <button v-on:click="f1">f1 filter /Foo/</button>
    <button v-on:click="f2">f2 concat arr</button>
    <button v-on:click="f3">f3 splice(2,3)</button>
    <button v-on:click="f4">f4 other functions</button>
<!--
    <button v-on:click="f5(item)">this.items.splice(index, 1)</button>
    <button v-on:click="f6(item)">f6 remove items</button>

        <template v-for = "uid in uids" track-by = "$index">
            <li>{{$index}}.{{uid._uid}}</li>
        </template>

        <div v-for = "value in user">{{$key}} : {{value}}
        </div>

        <div v-for = "(key, val) in user">{{val}} : {{key}}
        </div>
        </br>

-->

  </div>
</template>

<script>
  export default {
    name: 'test',
    data() {
      return {
        blogUrl: 'http://codingexplained.com',
        message: 'hello world!',
        movieTitle: 'The matrix',
        movieTitles: ['The matrix', 'The matrix reload','The matrix revolutions'],
        releaseYear: 1999,
        itemsInStock: 0,
        company: 'VueX Ltd.',
        showName: true,
        isA: true,
        isB: true,

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
        movies: [
          { mName: 'The Matrix', year: 1999 },
          { mName: 'The Matrix Reloaded', year: 2000 },
          { mName: 'The Matrix Revoultions', year: 2003 }
        ],
        items: [
          { msg: 'Foo'},
          { msg: 'Bar'},
          { msg: 'George'},
          { msg: 'John'},
          { msg: 'Tom'},
          { msg: 'James'},
          { msg: 'Martin'}
        ],
        arr: [
          { msg: 'array 1'},
          { msg: 'array 2'},
          { msg: 'array 1'}
        ],
        uids: [
          { _uid: '88f869d'},
          { _uid: '7496c10'}
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

      addMovie: function () {
        this.movies.push({
          mName: 'The Fast and the Furious',
          year: 2001
        });
      },

      f1: function() {
        this.items = this.items.filter(function(item){
            return item.msg.match(/Foo/)
        });
      },

      f2: function() {
        this.items = this.items.concat(this.arr[0])
        this.items = this.items.concat(this.arr[1])
        this.items = this.items.concat(this.arr[2])
      },

      f3: function() {
        this.items = this.items.splice(2,3)
      },

      f4: function() {
        this.items.pop();
        this.items.push({msg:'push item'});
        this.items.shift();
        this.items.unshift();
        this.items.sort();
        this.items.reverse();
      },

      f5: function(item) {
         var index = this.items.indexOf(item);
         if (index !== -1){
           this.items.splice(index,1);
         }
      },

      f6: function(item) {
        this.items.$remove(item);
      },

    },

    computed: {
      getFullName: function() {
        return this.user.firstName + ' '+ this.user.lastName;
      },
      formattedMovies: function() {
        return this.movies.map ( function(movie){
          return movie.mName + ' (' + movie.year +')';
        });
      },
    },
    watch: {
      movies: function (movies){
        var newMovie = movies[movies.length -1];
        alert(newMovie.mName + ' from ' + newMovie.year + ' was just added');
      }
    },

    filters: {
      uppercase: function(value, onlyFirstCharavter) {
        if (!value) {
          return '';
        }

        value = value.toString();

        if (onlyFirstCharavter){
          return value.charAt(0).toUpperCase() + value.slice(1);
        }
        else{
          return value.toUpperCase();
        }
      },

      removeSpaces: function(value){
        if (!value) {
          return '';
        }
        return value.toString().replace(/ /g, '');
      }
    },
}
</script>

<style scoped>

  .static {
    font-size: 20px;
    width: 600px;
    margin: 0 auto;
    background-color: yellow;
    height: 40px;
    line-height: 40px;
    text-align: center;
  }

  .class-a {
    color: #FF0000;
  }

  .class-b {
    color: green;
    text-decoration: underline;
  }

</style>
