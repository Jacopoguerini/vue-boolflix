<template>
    <main>

        <section v-if="movies.length > 0">
            <p>La ricerca ha prodotto questi risultati in  <span>Film</span>:</p>
            <div class="container">
                <Item
                v-for="item in movies"
                :key="item.id"
                :item="item"/>
            </div>
        </section>

        <section v-else-if="series.length > 0">
            <p>La ricerca ha prodotto questi risultati in <span>Serie TV</span>:</p>
            <div class="container">
                <Item
                v-for="item in series"
                :key="item.id"
                :item="item"/>
            </div>

        </section>

        <div v-else>La tua ricerca non ha prodotto risultati.</div>
        
    </main>
</template>

<script>
import Item from './Item';

export default {
    name: "Main",
    props: {
        "movies": Array,
        "series": Array,
        "item": Object
    },
    components: {
        Item,
    }
}
</script>

<style lang="scss" scoped>
    span {
        text-transform: uppercase;
    }

    .container {
        height: calc(100% - 80px);
        width: 80%;
        margin: 0 auto;
        background-color: lightgrey;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        align-items: center;
        padding: 30px;
    }

</style>