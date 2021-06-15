<template>
    <main>

        <section>

            <p>{{ searchProductionText }}<span>{{ moviesSearchSpan }}</span>:</p>

            <div class="container">
                <Item
                v-for="item in movies"
                :key="item.id"
                :item="item"/>
            </div>

        </section>

        <section>

            <p>{{ searchProductionText }} <span>{{ seriesSearchSpan }}</span>:</p>

            <div class="container">
                <Item
                v-for="item in series"
                :key="item.id"
                :item="item"/>
            </div>
            
        </section>

        
                
    </main>
</template>

<script>
import Item from './Item';

export default {
    name: "Main",
    data: function() {
        return {
            searchProductionText: "La tua ricerca ha prodotto questi risultati in ",
            moviesSearchSpan: "MOVIES",
            seriesSearchSpan: "SERIE TV",
            noResultsText: "La tua ricerca non ha prodotto alcun risultato"
        }
    },
    props: {
        "movies": Array,
        "series": Array,
        "item": Object
    },
    components: {
        Item,
    },
    methods: {

    }
}
</script>

<style lang="scss" scoped>
    p {
        padding: 30px 30px 0 30px;
        font-size: 20px;
    }

    .container {
        height: calc(100% - 80px);
        width: 80%;
        margin: 0 auto;
        background-color: lightgrey;
        display: flex;
        flex-wrap: wrap;
        justify-content: flex-start;
        align-items: center;
        padding: 30px;
    }

</style>