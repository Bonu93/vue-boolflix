<template>
  <div id="app">
    <Header @search="getQuery" />
    <Main />
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import Main from '@/components/Main.vue'
import axios from "axios"

export default {
  name: 'App',
  components: {
    Header, 
    Main,
  },
    
  data() {
    return {
      movies: [],
      query: '',
    }
  },

  created() {
    this.getMovies();
  },

  methods: {
    getMovies() {
      axios
        .get("https://api.themoviedb.org/3/search/movie/?api_key=97334a30f0eef5e4d8fc3009e75f736b&query=pallone")
        .then((result) => {
          console.log(result.data.results);
          this.movies = result.data.results;
        })
    },

    getQuery(text) {
      this.query = text;
    },
  },
    
  
}
</script>

<style lang="scss">
#app {
 
}
</style>
