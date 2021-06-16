<template>
  <div id="app">

    <Header 
    @performSearch="searchTitle" />

    <div v-if="movies.length != 0 && series.length != 0">
      <div @click="resetSearch">Prova a resettare</div>

      <Main
      :movies="movies"  
      :series="series"/>
    </div>

    <div v-else class="default-image">

    </div>

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
    resetSearch: function() {
      this.movies = [];
      this.series = [];
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
            language: "it-IT",
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

  .default-image {
    width: 100%;
    height: calc(100% - 70px);
    background-image: url(https://assets.nflxext.com/ffe/siteui/vlv3/c0a32732-b033-43b3-be2a-8fee037a6146/ac84d843-0e4d-4bff-9992-7dd636827a40/IT-it-20210607-popsignuptwoweeks-perspective_alpha_website_large.jpg);
  }
}

</style>
