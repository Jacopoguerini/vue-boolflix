<template>
    <div class="item">
        
        <img v-if="item.poster_path != null" :src="imgUrlRoot + item.poster_path" :alt="item.title">
        <img v-else src="https://cdn.bookauthority.org/dist/images/book-cover-not-available.6b5a104fa66be4eec4fd16aebd34fe04.png" alt="">
        <!-- <img v-else src="https://cdn.bookauthority.org/dist/images/book-cover-not-available.6b5a104fa66be4eec4fd16aebd34fe04.png" :alt="item.title"> -->

        <div class="details">
            <h3>{{
                item.title ?
                item.title :
                item.name                
            }}</h3>


            <h4>{{
                item.original_title ?
                item.original_title :
                item.original_name
            }}</h4>

            
            <!-- Scartata ipotesi v-if per visualizzare l'immagine -->
            <!-- <img
            :src="require(`..assets/img/${item.original_language}.png`)"
            :alt="`bandiera ${item.original_language}`"
            v-if="flags.includes(item.original_language)"> -->
            <!-- <p v-else>{{ item.original_language }}</p> -->

            <lang-flag :iso="item.original_language" :squared="false"/>

            <div class="stars">
                <i v-for="i in 5" :key="i"
                :class="i <= voteRound(item) ? 'fas fa-star' : 'far fa-star'">
                </i>

                <p>{{item.vote_average}}/10</p>
            </div>

            <p class="overview">
                {{ item.overview }}
            </p>

        </div>
            
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
    name: "Item",
    data: function() {
        return {
            imgUrlRoot: 'https://image.tmdb.org/t/p/w342',
            flags: ['it', 'en']
        }
    },
    props: {
        "item": Object
    },
    components: {
        LangFlag
    },
    methods: {
        voteRound: function(element) {
            return Math.round((element.vote_average / 2));
        }
    }
}
</script>

<style lang="scss" scoped>

    .item {
        width: calc(20% - 20px);
        height: 350px;
        margin: 0 10px 30px 10px;
        color: white;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        position: relative;

        img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .details {
            width: 100%;
            height: 100%;
            padding: 15px;
            background-color: rgba(0, 0, 0, 0.8);
            position: absolute;
            word-wrap: break-word;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            opacity: 0;

            &:hover {
                opacity: 1
            }
            
            & > *:not(:last-child) {
                margin-bottom: 15px;
            }
            h3, h4 {
                text-align: center;
            }
            span {
                font-size: 12px;
            }


            .stars {
                text-align: center;
                .fas {
                    color: gold;
                }
                .far {
                    color: goldenrod;
                }
            }

            .overview {
                max-height: 40%;
                overflow-y: scroll;
                &::-webkit-scrollbar {
                width: 8px;
                }
                &::-webkit-scrollbar-track {
                background: #f1f1f1;
                border-radius: 10px;
                }
                &::-webkit-scrollbar-thumb {
                background: grey;
                border-radius: 10px;
                }
                &::-webkit-scrollbar-thumb:hover {
                background: rgb(87, 87, 87);
                }
            }
       }
    }


</style>