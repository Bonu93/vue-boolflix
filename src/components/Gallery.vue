<template>

    <div class="gallery container" v-show="listOk"> 
        <div class="row g-0">
                <div class="item col-12 col-sm-6 col-md-3 p-1"
                v-for="(item, i) in list" 
                :key="`item-${i}`"
                >
                    <Card 
                    :title="item.title ? item.title : item.name"
                    :orTitle="item.original_title ? item.original_title : item.original_name"
                    :language="item.original_language"
                    :vote="item.vote_average"
                    :image="item.poster_path"
                    :overview="item.overview"
                    />
                </div>
            
        </div>
        

        
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
    

<style lang="scss" scoped>
    .item {
        height: 500px;
    }
</style>
