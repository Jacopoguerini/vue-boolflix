<template>
    <header>
        <a href="#">
            <img src="../assets/img/logo.png" alt="Logo Image">
        </a>
        
        <div class="search-bar">
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
        </div>
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
        height: 70px;
        background-color: grey;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 100px;

        a {
            height: 100%;
            display: flex;
            align-items: center;

            img {
                height: 70%;
            }
        }

        .search-bar {

            input {
                height: 40%;
                padding-left: 5px;
                width: 250px;

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
    }


</style>