<template>
    <main>
        <section v-if="movies.length > 0">
            <p>La tua ricerca di "{{ currentSearchText }}" ha prodotto questi risultati in {{ moviesSearchSpan }}:</p>

            <div class="container">
                <Item
                v-for="item in movies"
                :key="item.id"
                :item="item"/>
            </div>

            <!-- <div class="next-prev">
                <span @click="prevMoviePage">
                    <i class="fas fa-chevron-left"></i>
                    Pagina Precedente
                </span>
                <span
                v-if="moviesPage <= totalMoviePages"
                @click="nextMoviePage">
                    Pagina Successiva
                    <i class="fas fa-chevron-right"></i>
                </span>
            </div> -->
        </section>
        <!-- <p v-else>La tua ricerca non ha prodotto risultati in {{moviesSearchSpan}}!</p> -->

        <section v-if="series.length > 0">
            <p>La tua ricerca di "{{ currentSearchText }}" ha prodotto questi risultati in {{ seriesSearchSpan }}:</p>

            <div class="container">
                <Item
                v-for="item in series"
                :key="item.id"
                :item="item"/>
            </div>

        </section>
        <!-- <p v-else>La tua ricerca non ha prodotto risultati in {{ seriesSearchSpan }}!</p> -->

        <!-- <p v-if="movies.length == 0 && series.length == 0">Nessun risultato per la tua ricerca.</p> -->
                
    </main>
</template>

<script>
import Item from './Item';

export default {
    name: "Main",
    data: function() {
        return {
            moviesSearchSpan: "FILM",
            seriesSearchSpan: "SERIE TV",
        }
    },
    props: {
        "movies": Array,
        "series": Array,
        "currentSearchText": String,
        "moviesPage": Number,
        "totalMoviePages": Number,
        "seriesPage": Number        
    },
    components: {
        Item
    },
    methods: {
        nextMoviePage: function() {
            this.$emit('nextMoviePage', this.moviesPage);
        },
        prevMoviePage: function() {
            this.$emit('prevMoviePage', this.moviesPage);
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../style/general.scss';

    main {
        color: white;

        // .next-prev {
        //     text-align: center;

        //     span {
        //         margin: 0 15px 0 15px;
        //         padding: 5px 15px;
        //         cursor: pointer;
        //         border: 1px solid white;
        //         border-radius: 5px;
        //     }
        // }
    }

    p {
        padding: 30px 0 15px 30px;
        font-size: 20px;
    }

    .container {
        height: calc(100% - 80px);
        width: 80%;
        margin: 0 auto;
        display: flex;
        flex-wrap: wrap;
        justify-content: flex-start;
        align-items: center;
        padding: 30px 0 30px;
        position: relative;
    }

</style>