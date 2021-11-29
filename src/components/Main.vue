<template>
    <main>
        <div class="gallery">
            <Card 
            v-for="(movie, i) in moviesList" :key="`movie-${i}`"
            :title="movie.title"
            :orTitle="movie.original_title"
            :language="movie.original_language"
            :vote="movie.vote_average"
            />
        </div>

        
    </main>
</template>

<script>
import Card from '@/components/Card.vue'

export default {
    name: "Main",
    props: {
        moviesList: Array,
    },
    components: {
        Card,
    }, 
};
</script>

<style lang="scss" scoped></style>
