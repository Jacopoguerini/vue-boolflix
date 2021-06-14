<template>
    <header>
        <input
        type="text"
        placeholder="Titoli"
        v-model="currentSearchText"
        @keyup.enter="$emit('performSearch', currentSearchText)">
        
        <span
        class="btn search-btn"
        @click="$emit('performSearch', currentSearchText)">
        <i class="fas fa-search"></i>
        Cerca</span>
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
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../style/general.scss';

    header {
        height: 80px;
        background-color: grey;
        display: flex;
        justify-content: flex-end;
        align-items: center;
        padding: 0 100px;

        input {
            height: 40%;
            padding-left: 5px;

            &:focus {
            outline: none
            }
            &::placeholder {
                color: grey;
            }
        }


        .fa-search {
            margin-right: 10px;
        }
    }


</style>