<template>
    <ul>
        <li>Titolo: {{ title }}</li>
        <li v-show="titleOk">Titolo originale: {{ orTitle }}</li>
        <li class="lang-img" v-if="flagOk">
            <img :src="require(`@/assets/${language}.png`)" alt="">
        </li>
        <li v-else>Lingua: {{ language }}</li>
        <li>Voto: {{ vote }}</li>
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
</style>