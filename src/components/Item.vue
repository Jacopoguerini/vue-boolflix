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

            <span>{{
                item.release_date ?
                getYear(item.release_date) :
                getYear(item.first_air_date)
            }}</span>
            
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

                <p>{{item.vote_average}}<span id="max-vote">/10</span></p>
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
        },
        getYear: function(element) {
            return element.substr(0, 4);
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
        transition: transform 0.2s;

        &:hover {
            transform: scale(1.2);
            z-index: 1000;
            box-shadow: 0 0 10px lightgray;
        }

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

            h3 {
                margin-bottom: 5px;
            }
            h4 {
                font-size: 12px;
                margin-bottom: 15px;
            }
            h3, h4 {
                text-align: center;
            }
            span {
                font-size: 12px;
                margin-bottom: 10px;
            }


            .stars {
                margin-bottom: 15px;
                text-align: center;

                i {
                    margin-bottom: 5px;
                }

                .fas {
                    color: gold;
                }
                .far {
                    color: goldenrod;
                }
            }

            .overview {
                max-height: 50%;
                overflow-y: auto;
                &::-webkit-scrollbar {
                width: 8px;
                }
                &::-webkit-scrollbar-track {
                background: #f1f1f1;
                border-radius: 5px;
                }
                &::-webkit-scrollbar-thumb {
                background: grey;
                border-radius: 5px;
                }
                &::-webkit-scrollbar-thumb:hover {
                background: rgb(87, 87, 87);
                }
            }

            #max-vote {
                font-size: 10px;
            }
       }
    }


</style>