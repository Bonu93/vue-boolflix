<template>
  <div id="app" class="h-100 bg-prim d-flex flex-column">
    <Header @search="getResearch" />
    <main class="overflow-auto flex-grow-1 text-light p-4">
      <h2>FILM</h2>
      <Gallery :list="movies"/>
      <h2>SERIE TV</h2>
      <Gallery :list="series"/>

    </main>
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import Gallery from '@/components/Gallery.vue'
import axios from "axios"

export default {
  name: 'App',
  components: {
    Header, 
    Gallery,
  },
    
  data() {
    return {
      movies: [],
      series: [],
      query: '',
    }
  },

  created() {
    this.getPopMovies();
    this.getPopSeries();
  },

  methods: {
    
    getPopSeries ()  {
      axios.get('https://api.themoviedb.org/3/tv/popular', {
        params: {
          api_key: '97334a30f0eef5e4d8fc3009e75f736b',
                language: 'it',
                page: 1,
                
        }
      })
      .then((result) => {
        this.series = result.data.results;
      })
    },

    getPopMovies() {
      axios.get('https://api.themoviedb.org/3/movie/popular', {
        params: {
          api_key: '97334a30f0eef5e4d8fc3009e75f736b',
                language: 'it',
                page: 1,
                
        }
      })
      .then((result) => {
        this.movies = result.data.results;
      })
        
    },
    getMovies() {
      axios
        .get('https://api.themoviedb.org/3/search/movie' , {
            params: {
                api_key: '97334a30f0eef5e4d8fc3009e75f736b',
                language: 'it',
                query: this.query,
              }
        })
        .then((result) => {
          this.movies = result.data.results;
        })
    },

    getSeries() {
      axios
        .get('https://api.themoviedb.org/3/search/tv' , {
            params: {
              api_key: '97334a30f0eef5e4d8fc3009e75f736b',
              language: 'it',
              query: this.query,
            }
        })
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
  @import '@/styles/globals.scss';

  main {
    text-align: center;
  }

</style>
