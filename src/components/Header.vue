<template>
    <header>
        <input
        type="text"
        placeholder="Titoli, persone, generi"
        v-model.trim="currentSearchText"
        @keyup="$emit('performSearch', currentSearchText)">
    </header>
</template>

<script>


export default {
    name: "Header",
    data: function() {
        return {
            currentSearchText: ''
        }
    },
    methods: {
        performSearch: function(text) {
            this.currentSearchText = text;           
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