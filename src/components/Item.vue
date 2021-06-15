<template>
    <div class="item">
        <div class="title">
            <h3>{{ item.title }}</h3>
            <h3>{{ item.name }}</h3>
        </div>

        <div class="og-title">
            <h4>{{ item.original_title }}</h4>
            <h4>{{ item.original_name }}</h4>
        </div>
        
        <!-- Scartata ipotesi di usare v-if e funzione per visualizzare l'immagine della lingua-->
        <lang-flag :iso="item.original_language" :squared="false"/>

        <p>{{ item.vote_average }}</p>
            
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
    name: "Item",
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
        padding: 15px;
        border: 1px solid black;
        word-wrap: break-word;
        margin: 0 10px 20px 0;

        h3, h4, p {
            text-align: center;
        }
    }


</style>