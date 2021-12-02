<template>
  <div id="app">
    <AppHeader @clickBtn = 'userSearch'/>
    
    <FilmLibrary 
    :moviesList= 'filmsList'
    :tvList= 'tvSeries'
    />
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
    FilmLibrary,
  },
  data() {
    return {
      apiUrl: 'https://api.themoviedb.org/3/search/',
      apiKey: '0e7cd09201aa25f0f40469f08d9be41c',
      filmsList : [],
      tvSeries: []
      // searchedFilm : ''
    }
  },
  props: {

  },
  // created() {
  //   this.getFilm(this.apiParams);
  // },
  // computed: {
  //   filmSeries() {
  //     return [...this.filmsList,...this.tvSeries]
  //   }

  // },
  methods: {
    getFilm: function(apiParams) {
      axios
      .get(this.apiUrl +'movie',apiParams)
      .then((result) => {
        this.filmsList = result.data.results;
        console.log("film",this.filmsList);

      
      })
      .catch((error) => {
        console.log('errore', error);
      })
       
    },
    getTvSeries: function(apiParams) {
      axios
      .get(this.apiUrl +'tv',apiParams)
      .then((result) => {
        this.tvSeries = result.data.results;
        console.log("serie",this.tvSeries);

      
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
      this.getTvSeries(paramsSearch);
      
  

    } 

  }
}
</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.min.css';
body {
  background-color: #434343;
}
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

#app {
  
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
