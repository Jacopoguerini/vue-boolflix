<template>
    <header>
        <input
        type="text"
        placeholder="Titoli, persone, generi"
        v-model="currentSearchText"
        @keyup="$emit('performSearch', currentSearchText)">
        
        <span
        class="btn search-btn"
        @click="$emit('performSearch', currentSearchText)">
        Cerca</span>
        
        <span
        class="btn reset-btn"
        @click="$emit('reset', currentSearchText)">
        Reset</span>
    </header>
</template>

<script>


export default {
    name: "Header",
    data: function() {
        return {
            currentSearchText: ""
        }
    },
    methods: {
        performSearch: function(text) {
            this.currentSearchText = text;      
        },
        reset: function() {
            this.currentSearchText = "";
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

    .btn {
        text-transform: uppercase;
        cursor: pointer;
        margin-left: 15px;
        padding: 5px 25px;
        background-color: red;
        font-size: 16px;
    }
</style>