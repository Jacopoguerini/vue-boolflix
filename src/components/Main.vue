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
        "currentSearchText": String
    },
    components: {
        Item
    }
}
</script>

<style lang="scss" scoped>
@import '../style/general.scss';

    main {
        color: white;
    }

    p {
        padding: 30px 0 0 30px;
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