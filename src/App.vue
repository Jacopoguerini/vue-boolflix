<template>
  <div id="app">

    <Header 
    @performSearch="searchTitle"
    @resetSearch="resetSearch" />

    <div
    v-if="movies.length == 0 && series.length == 0"
    class="default-image">

      <div class="main-title">
        <h1>Inizia qui la tua ricerca.</h1>
        <h2>Film e serie tv sono a portata di un click.</h2>
      </div>

    </div>

    <div v-else>

      <Main
      :movies="movies"  
      :series="series"
      :currentSearchText="currentSearchText"
      :moviesPage="moviesPage"
      :totalMoviePages="totalMoviePages"
      :seriesPage="seriesPage"
      @nextMoviePage="nextMoviePage"
      @prevMoviePage="prevMoviePage" />
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
      series: [],
      moviesPage: 1,
      totalMoviePages: 0,
      seriesPage: 1
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
      this.moviesPage = 1;
    },
    getMovies: function() {
      axios
        .get(this.apiMovieUrl, {
          params: {
            api_key: this.apiKey,
            query: this.currentSearchText,
            language: "it-IT",
            page: this.moviesPage
          }
        })
        .then(
          res => {
            this.movies = res.data.results;
            this.moviesPage = 1;
            this.totalMoviePages = res.data.total_pages;
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
            page: this.seriesPage
          }
        })
        .then(
          res => {
            this.series = res.data.results;
          }
        );
    }
    // nextMoviePage: function() {
    //   axios
    //     .get(this.apiMovieUrl, {
    //       params: {
    //         api_key: this.apiKey,
    //         query: this.currentSearchText,
    //         language: "it-IT",
    //         page: this.moviesPage
    //       }
    //     })
    //     .then(
    //       res => {
    //         this.movies = res.data.results;
    //         this.moviesPage ++;
    //       }
    //     );
    // },
    // prevMoviePage: function() {
    //   this.moviesPage --;
    //   axios
    //     .get(this.apiMovieUrl, {
    //       params: {
    //         api_key: this.apiKey,
    //         query: this.currentSearchText,
    //         language: "it-IT",
    //         page: this.moviesPage
    //       }
    //     })
    //     .then(
    //       res => {
    //         this.movies = res.data.results;
    //       }
    //     );
    // }
  }
}
</script>

<style lang="scss">
@import './style/general.scss';

#app {
  height: 100vh;
  background-color: black;
  overflow-x: hidden;
  overflow-y: auto;

  .default-image {
    width: 100%;
    height: calc(100% - 70px);
    background-image: url(https://assets.nflxext.com/ffe/siteui/vlv3/c0a32732-b033-43b3-be2a-8fee037a6146/ac84d843-0e4d-4bff-9992-7dd636827a40/IT-it-20210607-popsignuptwoweeks-perspective_alpha_website_large.jpg);

    .main-title {
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.4);
      color: white;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;

    }
    h1 {
      font-size: 70px;
      margin-bottom: 20px;
    }
    h2 {
      font-size: 40px;
    }
  }
}

</style>
