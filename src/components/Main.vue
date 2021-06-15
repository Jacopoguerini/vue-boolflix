<template>
    <main>
        <div v-if="items.length > 0" class="container">
            <Item
            v-for="item in items"
            :key="item.id"
            :item="item"/>
        </div>
        <div v-else>La tua ricerca non ha prodotto risultati.</div>
        
    </main>
</template>

<script>
import Item from './Item';

export default {
    name: "Main",
    props: {
        "items": Array,
        "item": Object
    },
    components: {
        Item,
    }
}
</script>

<style lang="scss" scoped>
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