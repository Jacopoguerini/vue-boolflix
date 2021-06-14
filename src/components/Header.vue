<template>
    <header>
        <input
        type="text"
        placeholder="Titoli, persone, generi"
        v-model.trim="searchText"
        @keyup="$emit('performSearch', searchFieldText)">
    </header>
</template>

<script>


export default {
    name: "Header",
    data: function() {
        return {
            searchFieldText: ''
        }
    },
    methods: {
        performSearch: function(text) {
            this.searchFieldText = text;
            console.log(this.searchFieldText);
        }
    }
}
</script>

<style lang="scss" scoped>
    header {
        height: 80px;
        background-color: grey;
        display: flex;
        justify-content: flex-end;
        align-items: center;
        padding: 0 100px;
    }
</style>