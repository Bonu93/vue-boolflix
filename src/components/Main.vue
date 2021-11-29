<template>
  <main>
      <div class="movies">
          <ul 
          v-for="(movie, i) in moviesList"
          :key="`movie-${i}`"
          >

            <li>
                Titolo: {{ movie.title }}
            </li>
             <li>
                Titolo originale: {{ movie.original_title }}
            </li>
             <li>
                Lingua: {{ movie.original_language }}
            </li>
             <li>
                Voto: {{ movie.vote_average }}
            </li>


          </ul>
      </div>
  </main>
</template>

<script>
export default {
    name: 'Main',
    props: {
        moviesList: Array,
    }
}
</script>

<style lang="scss" scoped>

</style>