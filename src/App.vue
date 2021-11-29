<template>
  <div id="app">
    <Header @search="getResearch" />
    <Main :moviesList="movies"/>
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

  },

  methods: {
    getMovies() {
      axios
        .get(`https://api.themoviedb.org/3/search/movie/?api_key=97334a30f0eef5e4d8fc3009e75f736b&query=${this.query}`)
        .then((result) => {
          this.movies = result.data.results;
        })
    },

    getResearch(text) {
      this.query = text;
      this.getMovies();
    },
  },
    
  
}
</script>

<style lang="scss">

</style>
