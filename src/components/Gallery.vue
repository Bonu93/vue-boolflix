<template>
    <div class="gallery">

        <section class="items-section"
        v-show="listOk"
        >
            <div class="item"
            v-for="(item, i) in list" 
            :key="`item-${i}`"
            >
                <Card 
                :title="item.title ? item.title : item.name"
                :orTitle="item.original_title ? item.original_title : item.original_name"
                :language="item.original_language"
                :vote="item.vote_average"
                :image="item.poster_path"
                />
            </div>
        </section>

        
    </div>
</template>

<script>
import Card from '@/components/Card.vue'

export default {
    name: "Main",
    props: {
        list: Array,
    },
    components: {
        Card,
    }, 

    computed: {
        listOk() {
           return this.list.length > 0 ?
                true : false
        },
    }
};
</script>

<style lang="scss" scoped></style>
