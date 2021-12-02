<template>
    <div id="tvseries">
        <img :src="baseUrl + sizeImg + posterPath" :alt= details.original_title>
        <h3>{{details.original_name}}</h3>
        <h4>{{details.name}}</h4>
        
        <div v-if="details.original_language === 'it' "><img class="flags" src= '../assets/img/ita-flag.png' alt="italy"></div>
        <div v-else-if="details.original_language === 'en' "><img class="flags" src= '../assets/img/greatbritain-flag.png' alt="greatbritain"></div>
        <div v-else><img class="flags" src='../assets/img/arco-flag.png' alt="arcobaleno">Lang= {{details.original_language}} </div>


        <!-- <div >{{voteBase5}} </div> -->
       <i v-for="n in voteBase5 " :key="n" class="fas fa-star full-star"> </i>
       <i v-for="y in 5 - voteBase5 " :key="y" class="far fa-star empty-star"></i>
        
        
    </div>
</template>

<script>
export default {
    name:"TvSeries",
    data() {
        return {
            baseUrl: 'https://image.tmdb.org/t/p/',
            sizeImg:'w342/',
            posterPath: this.details.poster_path, 
            originalVoteAvg: this.details.vote_average,
            voteBase5:'',
            
        }
    },

    props: {
        details: Object,
    },

    created() {
        this.vote1to5()
       
    },
    computed: {
        
    },

    methods : {
        vote1to5() {
            console.log(this.vote =this.originalVoteAvg / 2);
            return this.voteBase5 =Math.floor(this.originalVoteAvg / 2)
        },
        
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
.full-star {
    
    
}

</style>