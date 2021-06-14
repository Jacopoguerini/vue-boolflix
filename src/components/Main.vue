<template>
    <main>
        <div class="item" v-for="(item, index) in items" :key="index">
            <h1>{{ item.title }}</h1>
            <h3>{{ item.original_title }}</h3>
            <h4>{{ item.original_language }}</h4>
            <h5>{{ item.vote_average }}</h5>
        </div>
    </main>
</template>

<script>


export default {
    name: "Main",
    props: {
        items: Array
    }

}
</script>

<style lang="scss" scoped>
    main {
        height: calc(100vh - 80px);
        background-color: lightgrey;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        align-items: center;
        padding: 25px;
    }

    .item {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 15px;
        border: 1px solid blue;
        word-wrap: break-word;
        margin-bottom: 20px;
    }

</style>