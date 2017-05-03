<template>
  <div class="test">
    <a v-bind:href="blogUrl">Vist my blog</a>
    <h1>{{user.fullName.split(' ')[0]}}</h1>
    <h1>{{user.age > 60 ? 'old' : 'young'}}</h1>
    <p v-if = "showName">{{getFullName}}</P>
    <p v-else>Nobody</P>
    <P> Movie Title = {{movieTitle}}</p>
    <p> Release Year = {{releaseYear}}</p>
    <p> The Movie is {{isMovieOld(releaseYear) ? 'old' : 'new'}}</p>
    <div v-bind:title="movieTitle">Hover your mouse here to see movie title!</div>
    <ul>
      <li v-for = "item in items">{{item.title}}</li>
    </ul>
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
        user: {
          firstName: 'John',
          lastName: 'Smith',
          fullName: 'John Smith',
          age: 27
        },
        showName: true,
        items:[
          {title: 'Item one'},
          {title: 'Item two'},
          {title: 'Item three'}
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

</style>
