<template>
<section>
    <Film
     v-for ="movie, i in moviesList"
     :key="i"
     :details="movie"/>
</section>
</template>

<script>
// import axios from 'axios'
import Film from '../components/Film.vue'

export default {
    name:"FilmLibrary",
    components: {
        Film
    },
    data() {
        return {
          
        }
    },
    props: {
        moviesList: Array
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