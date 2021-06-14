<template>
  <div id="app">

    <Header 
    @performSearch="searchTitle" />

    <Main
    :searchText="currentSearchText"/>
  </div>
</template>

<script>
import Header from './components/Header';
import Main from './components/Main';


export default {
  name: 'App',
  data: function() {
    return {
      currentSearchText: ""
    }
  },
  components: {
    Header,
    Main
  },
  methods: {
    searchTitle: function(currentSearchText) {
      this.currentSearchText = currentSearchText;
    }
  }
}
</script>

<style lang="scss">
@import './style/general.scss';

#app {
  height: 100vh;
}

</style>
