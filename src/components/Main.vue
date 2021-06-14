<template>
    <main class="container">
        <div class="item" v-for="(item, index) in items" :key="index">
            <h1>{{ item.title }}</h1>
            <h3>{{ item.original_title }}</h3>
            <country-flag :country='item.original_language' size='normal'/>
            <h5>{{ item.vote_average }}</h5>
            
        </div>
    </main>
</template>

<script>
import CountryFlag from 'vue-country-flag';

export default {
    name: "Main",
    props: {
        items: Array,
    },
    components: {
        CountryFlag
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

        .item {
            width: calc(20% - 10px);
            height: 350px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 15px;
            border: 1px solid black;
            word-wrap: break-word;
            margin-bottom: 20px;

            h1, h3, h4, h5 {
                text-align: center;
            }
        }
    }

</style>