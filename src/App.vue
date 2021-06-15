<template>
  <div id="app">

    <Header 
    @performSearch="searchTitle" />

    <Main
    :movies="movies"
    :series="series"/>
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
      apiMovieUrl: 'https://api.themoviedb.org/3/search/movie',
      apiSeriesUrl: 'https://api.themoviedb.org/3/search/tv',
      apiKey: 'be21832a3253c3632ed774e5e919201f',
      currentSearchText: "",
      movies: [],
      series: []
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
      this.getSeries();
    },
    getMovies: function() {
      axios
        .get(this.apiMovieUrl, {
          params: {
            api_key: this.apiKey,
            query: this.currentSearchText,
            language: "it-IT"
          }
        })
        .then(
          res => {
            this.movies = res.data.results;
          }
        );
    },
    getSeries: function() {
      axios
        .get(this.apiSeriesUrl, {
          params: {
            api_key: this.apiKey,
            query: this.currentSearchText,
            language: "it-IT"
          }
        })
        .then(
          res => {
            this.series = res.data.results;
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
