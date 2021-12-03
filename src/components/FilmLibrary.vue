<template>
<section>
    <Film
    @clickFilm= 'getMovieCast'
     v-for ="movie in moviesList"
     :key="movie.id"
     :details="movie"
     :castArray= 'castList'
     :activeMovie= 'activeFilm'
     :idActive="activeId"
     :listGenre="genreList"
    />

    <TvSeries
    @clickTv= 'getTvCast'
     v-for = "tv in tvList"
     :key= "tv.id"
     :details= "tv"
     :castArray= 'castListTv'
     :activeTv= 'activeFilm'
     :idActive= "activeId"
     :listGenreTv= "genreListTv"
    />
</section>
</template>

<script>
import axios from 'axios'
import Film from '../components/Film.vue'
import TvSeries from '../components/TvSeries.vue'


export default {
    name:"FilmLibrary",
    components: {
        Film,
        TvSeries
    },
    data() {
        return {
        castList: [],
        castListTv: [],
        activeFilm: '',
        activeId:'',
        genreList:'',
        genreListTv:[]


        }
    },
    props: {
        moviesList: Array,
        tvList: Array
    },
    created() {
        
    },
    computed: {

    },
    methods: {
        getMovieCast(filmId) {
            axios
            .get('https://api.themoviedb.org/3/movie/'+filmId+'?api_key=0e7cd09201aa25f0f40469f08d9be41c&append_to_response=credits')
            .then((result) => {
                this.castList = result.data.credits.cast;
                this.genreList =result.data.genres;
                console.log("cast",this.castList);
            })
            
            this.activeId = filmId
            console.log(this.activeId);
            if (this.activeFilm === true) {
                this.activeFilm = false
                
            } else {
                this.activeFilm = true
                
            }
            
        
        },
         getTvCast(tvId) {
            axios
            .get('https://api.themoviedb.org/3/tv/'+tvId+'?api_key=0e7cd09201aa25f0f40469f08d9be41c&append_to_response=credits')
            .then((result) => {
                this.castListTv = result.data.credits.cast;
                this.genreListTv =result.data.genres;
                console.log("cast",this.castList);
            })
            
            this.activeId = tvId
            console.log(this.activeId);
            if (this.activeFilm === true) {
                this.activeFilm = false
                
            } else {
                this.activeFilm = true
                
            }
            
        
        },
        castSearch(clickId){
            const movieId = clickId
            this.getCast(movieId)
        }
    
        
    }


    

}
</script>

<style scoped lang="scss">
section {
    display: flex;
    flex-wrap: wrap;
    margin: 0 auto;
}

</style>