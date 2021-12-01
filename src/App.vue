<template>
  <div id="app">
    <AppHeader @clickBtn = 'userSearch'/>
    
    <FilmLibrary :moviesList= 'filmsList'/>
  </div>
</template>

<script>
import axios from 'axios'
import AppHeader from './components/AppHeader.vue'
import FilmLibrary from './components/FilmLibrary.vue'

export default {
  name: 'App',
  components: {
    AppHeader,
    FilmLibrary
  },
  data() {
    return {
      apiUrl: 'https://api.themoviedb.org/3/search/movie',
      apiKey: '0e7cd09201aa25f0f40469f08d9be41c',
      filmsList : [],
      // searchedFilm : ''
    }
  },
  props: {

  },
  // created() {
  //   this.getFilm(this.apiParams);
  // },
  computed: {

  },
  methods: {
    getFilm: function(apiParams) {
      axios
      .get(this.apiUrl,apiParams)
      .then((result) => {
        this.filmsList = result.data.results;
        console.log(this.filmsList);

      
      })
      .catch((error) => {
        console.log('errore', error);
      })
       
    },
    userSearch (inputText) {
      const paramsSearch= {
        params: {
          api_key: this.apiKey,
          query: inputText,
          language: 'it-IT'
        }
      }
      this.getFilm(paramsSearch);
      
  

    } 

  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
