<template>
    <main>
        <div v-for="(item, index) in searchedMovies" :key="index">

        </div>
    </main>
</template>

<script>
import axios from 'axios';

export default {
    name: "Main",
    data: function() {
        return {
            items: []
        }
    },
    props: {
        searchText: String
    },
    methods: {
        searchedMovies: function() {
            axios
                .get('https://api.themoviedb.org/3/search/movie', {
                    params: {
                        api_key: 'be21832a3253c3632ed774e5e919201f',
                        query: this.searchText,
                        language: "it-IT"
                    }
                })
                .then(
                    res => {
                        if(this.searchText == "") {
                            return this.items;
                        } else {
                            this.items.push(res.data.results);
                        }
                        return this.items;
                    }

                );
        }
        
    }
}
</script>

<style lang="scss" scoped>
    main {
        height: calc(100vh - 80px);
        background-color: lightgreen;
    }

</style>