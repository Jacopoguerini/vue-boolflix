<template>
  <div id="app">

    <Header 
    @performSearch="searchTitle" />

    <Main
    :items="items"/>
  </div>
</template>

<script>
import Header from './components/Header';
import Main from './components/Main';


import axios from 'axios';

export default {
  name: 'App',
  data: function() {
    return {
      currentSearchText: "",
      items: []
    }
  },
  components: {
    Header,
    Main
  },
  methods: {
    searchTitle: function(currentSearchText) {
      this.currentSearchText = currentSearchText;
      this.getMovies();
    },
    getMovies: function() {
      axios
        .get('https://api.themoviedb.org/3/search/movie', {
          params: {
            api_key: 'be21832a3253c3632ed774e5e919201f',
            query: this.currentSearchText,
            language: "it-IT"
          }
        })
        .then(
          res => {
            this.items = res.data.results;
          }
        );
    }
  }
}
</script>

<style lang="scss">
@import './style/general.scss';

#app {
  height: 100vh;
  background-color: lightgrey;
  overflow-x: hidden;
  overflow-y: auto;
}

</style>
