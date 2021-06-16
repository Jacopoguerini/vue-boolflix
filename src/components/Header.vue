<template>
    <header>
        <a href="#">
            <img src="../assets/img/logo.png" alt="Logo Image">
        </a>
        
        <div class="search-bar">
            <input
                type="text"
                placeholder="Titoli, film e serie"
                v-model="currentSearchText"
                @keyup.enter="performSearch">
                
            <span
            class="btn search-btn"
            @click="performSearch">
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
        performSearch: function() {
            this.$emit('performSearch', this.currentSearchText);
            this.currentSearchText = '';
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../style/general.scss';

    header {
        height: 70px;
        background-color: black;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 50px;
        box-shadow: 0 0 20px grey;
        // position: fixed;
        // top: 0;
        // width: 100%;
        // z-index: 1000;

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