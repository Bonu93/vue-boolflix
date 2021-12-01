<template>
    <div class="boolflix-card">
        
        <img v-if="imageOk" :src="`https://image.tmdb.org/t/p/w342/${image}`" :alt="title">
        
        <img v-else src="@/assets/not-found.jpg" alt="">



        <div class="info p-4">
            <h2>
                Titolo: {{ title }}
            </h2>
            <h2 v-show="titleOk">
                Titolo originale: {{ orTitle }}
            </h2>
            <h3>
                Voto:
                <i class="fas fa-star"
                v-for="n in voteConverted"
                :key="`fullstar-${n}`"
                >
                </i>
                <i class="far fa-star"
                v-for="n in (5 - voteConverted)"
                :key="`emptystar-${n}`"
                >
                </i>
            </h3>
            <p>{{overview}}</p>
        </div>
<!-- 
        <li>Titolo: {{ title }}</li>
        <li v-show="titleOk">Titolo originale: {{ orTitle }}</li>
        <li>Voto:
            <i class="fas fa-star"
            v-for="n in voteConverted"
            :key="`fullstar-${n}`"
            >
            </i>
            <i class="far fa-star"
            v-for="n in (5 - voteConverted)"
            :key="`emptystar-${n}`"
            >
            </i>

        </li> -->
    </div>
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
        overview: String,
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

    .boolflix-card {
        display: flex;
        flex-direction: column;
        height: 100%;
        position: relative;
        cursor: pointer;
        
        &:hover {
            .info  {
                opacity: 1;
            }
        }
            img {
                width: 100%;
                height: 100%;
                object-fit: cover;
            }
            .info {
                position: absolute;
                top: 0;
                left: 0;
                background-color: rgba(0, 0, 0, .7);
                width: 100%;
                height: 100%;
                white-space: normal;
                overflow: hidden;
                opacity: 0;
                transition: opacity .3s linear;
                
               
                h2,
                h3 {
                    font-size: 1.5rem;
                }
                p {
                    font-size: 1rem;
                    line-height: 1rem;
                }
                i {
                    color: yellow;
                }

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