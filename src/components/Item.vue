<template>
    <div class="item">
        
        <img :src="imgUrlRoot + item.poster_path" :alt="item.title">

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
                <i
                class="far fa-star">
                </i>
            </div>

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
    }
}
</script>

<style lang="scss" scoped>

    .item {
        width: 20%;
        height: 350px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin-bottom: 30px;
        position: relative;
        color: white;
        padding: 15px;

        img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .details {
            width: 80%;
            position: absolute;
            word-wrap: break-word;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
                
            h3, h4 {
                text-align: center;
            }
            
            & > * {
                margin: 10px 0;
            }
        }
    }


</style>