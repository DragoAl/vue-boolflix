<template>
<section>
    <Film
    @clickFilm= 'getCast'
     v-for ="movie in moviesList"
     :key="movie.id"
     :details="movie"
     :castArray= 'castList'
     :activeMovie= 'activeFilm'
     :idActive="activeId"
    />
    <TvSeries
     v-for ="tv in tvList"
     :key="tv.id"
     :details="tv"
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
        activeFilm: '',
        activeId:''


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
        getCast(filmId) {
            axios
            .get('https://api.themoviedb.org/3/movie/'+filmId+'?api_key=0e7cd09201aa25f0f40469f08d9be41c&append_to_response=credits')
            .then((result) => {
                this.castList = result.data.credits.cast;
                console.log("cast",this.castList);
            })
            
            this.activeId = filmId
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