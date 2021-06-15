<template>
    <div class="item">
        
        <img :src="imgUrlRoot + item.poster_path" :alt="item.title">

        <div class="details">
            <div class="title">
                <h3>{{ item.title }}</h3>
                <h3>{{ item.name }}</h3>
            </div>

            <div class="og-title">
                <h4>{{ item.original_title }}</h4>
                <h4>{{ item.original_name }}</h4>
            </div>
            
            <!-- Scartata ipotesi di usare v-if e funzione per visualizzare l'immagine della lingua -->

            <lang-flag :iso="item.original_language" :squared="false"/>

            <p>{{ item.vote_average }}</p>
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
            stars: 0
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
        width: calc(20% - 10px);
        height: 350px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin: 0 10px 20px 0;
        position: relative;

        img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .details {
            position: absolute;
            word-wrap: break-word;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;

            h3, h4, p {
                text-align: center;
        }
        }
    }


</style>