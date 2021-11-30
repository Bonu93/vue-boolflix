<template>
  <div id="app">
    <Header @search="getResearch" />
    <Main :moviesList="movies"
          :seriesList="series"
    />
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
      series: [],
      query: '',
    }
  },

  created() {

  },

  methods: {
    getMovies() {
      axios
        .get(`https://api.themoviedb.org/3/search/movie/?api_key=97334a30f0eef5e4d8fc3009e75f736b&language=it-IT&query=${this.query}`)
        .then((result) => {
          this.movies = result.data.results;
        })
    },

    getSeries() {
      axios
        .get(`https://api.themoviedb.org/3/search/tv?api_key=97334a30f0eef5e4d8fc3009e75f736b&language=it-IT&query=${this.query}`)
        .then((result) => {
          this.series = result.data.results;
        })
    },

    getResearch(text) {
      this.query = text;
      if (this.query !== '') {
        this.getMovies();
        this.getSeries();
      }
    },
      
  },
    
  
}
</script>

<style lang="scss">

</style>
