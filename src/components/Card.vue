<template>
    <ul>
        <li v-if="imageOk">
            <img :src="`https://image.tmdb.org/t/p/w185/${image}`" :alt="title">
        </li>
        <li v-else class="imgnotOk">
            Image not found
        </li>
        <li>Titolo: {{ title }}</li>
        <li v-show="titleOk">Titolo originale: {{ orTitle }}</li>
        <li class="lang-img" v-if="flagOk">
            Lingua:
            <img :src="require(`@/assets/${language}.png`)" alt="">
        </li>
        <li v-else>Lingua: {{ language }}</li>
        <li>
            <i class="fas fa-star"
            v-for="n in voteConverted"
            :key="`fullstar-${n}`"
            >
            </i>
            <i class="far fa-star"
            v-for="n in (5 - voteConverted)"
            :key="`fullstar-${n}`"
            >
            </i>

        </li>
    </ul>
</template>

<script>
export default {
    name: 'Card',
    props: {
        title: String,
        orTitle: String,
        language: String, 
        vote: Number,
        image: String,
    },

    data(){
        return {
            flags: [
                'en', 
                'it',
            ],
        }
    },

    computed: {
        flagOk() {
        return   this.flags.includes(this.language) ? 
                true : false;
        },

        titleOk() {
            return this.title !== this.orTitle ?
                true : false;
        },

        imageOk()  {
            return this.image !== null ?
                true : false;
        },

        voteConverted() {
            return Math.ceil(this.vote /2)
        }
    },
}
</script>

<style lang="scss" scoped>
    .lang-img {
        img {
            width: 30px;
        }
    }

    .imgnotOk {
        background-color: coral;
        display: flex;
        justify-content: center;
        align-items: center;
        width: 185px;
        height: 300px;
    }
</style>