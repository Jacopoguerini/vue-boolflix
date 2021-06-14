<template>
    <main>

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
    created: function() {
      axios
        .get('https://api.themoviedb.org/3/search/movie', {
            params: {
                api_key: 'be21832a3253c3632ed774e5e919201f',
                query: "",
                language: "it-IT"
            }
        })
        .then(
          
        );
    },
    methods: {
        
    }
}
</script>

<style lang="scss" scoped>
    main {
        height: calc(100vh - 80px);
        background-color: lightgreen;
    }

</style>