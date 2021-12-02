<template>
    <div id="tvseries">
        <img :src="baseUrl + sizeImg + posterPath" :alt= details.original_title>
        <h3>{{details.original_name}}</h3>
        <h4>{{details.name}}</h4>
        
        <div v-if="details.original_language === 'it' "><img class="flags" src= '../assets/img/ita-flag.png' alt="italy"></div>
        <div v-else-if="details.original_language === 'en' "><img class="flags" src= '../assets/img/greatbritain-flag.png' alt="greatbritain"></div>
        <div v-else><img class="flags" src='../assets/img/arco-flag.png' alt="arcobaleno">Lang= {{details.original_language}} </div>


        <div>{{details.vote_average}}</div>
        
        
    </div>
</template>

<script>
export default {
    name:"TvSeries",
    data() {
        return {
            baseUrl: 'https://image.tmdb.org/t/p/',
            sizeImg:'w342/',
            posterPath: this.details.poster_path 
        }
    },
    props: {
        details: Object,
    },
    methods : {

    }

}
</script>

<style scoped lang="scss">
#tvseries {
    margin: 30px;
}
.flags{
    width: 20px;
}

</style>