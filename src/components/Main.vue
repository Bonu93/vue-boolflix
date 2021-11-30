<template>
    <main>

        <section class="movie-section"
        v-show="moviesListOk"
        >
            <h2>Film</h2>
            <div class="movie"
            v-for="(movie, i) in moviesList" 
            :key="`movie-${i}`"
            >
                <Card 
                :title="movie.title"
                :orTitle="movie.original_title"
                :language="movie.original_language"
                :vote="movie.vote_average"
                :image="movie.poster_path"
                />
            </div>
        </section>


        <section class="series-section"
        v-show="seriesListOk"
        >

            <h2>Serie TV</h2>
            <div class="series"
            v-for="(series, i) in seriesList" 
            :key="`series-${i}`"
            >
                    <Card 
                    :title="series.name"
                    :orTitle="series.original_name"
                    :language="series.original_language"
                    :vote="series.vote_average"
                    :image="series.poster_path"
                    />
            </div>
        </section>

        
    </main>
</template>

<script>
import Card from '@/components/Card.vue'

export default {
    name: "Main",
    props: {
        moviesList: Array,
        seriesList: Array, 
    },
    components: {
        Card,
    }, 

    computed: {
        moviesListOk() {
           return this.moviesList.length > 0 ?
                true : false
        },

        seriesListOk() {
           return this.seriesList.length > 0 ?
                true : false
        },
    }
};
</script>

<style lang="scss" scoped></style>
