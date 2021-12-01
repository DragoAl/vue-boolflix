<template>
<section>
    <Film
     v-for ="movie in moviesList"
     :key="movie.id"
     :details="movie"
    />
    <TvSeries
     v-for ="tv in tvList"
     :key="tv.id"
     :details="tv"
    />
</section>
</template>

<script>
// import axios from 'axios'
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
          
        }
    },
    props: {
        moviesList: Array,
        tvList: Array
    },
    created() {
        
    },
    comupted: {

    },
    methods: {
       

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