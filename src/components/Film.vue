<template>
    <div id="movie">
        <img :src="baseUrl + sizeImg + posterPath" :alt= details.original_title>
        <h3>{{details.original_title}}</h3>
        <h4>{{details.title}}</h4>
        
        <div v-if="details.original_language === 'it' "><img class="flags" src= '../assets/img/ita-flag.png' alt="italy"></div>
        <div v-else-if="details.original_language === 'en' "><img class="flags" src= '../assets/img/greatbritain-flag.png' alt="greatbritain"></div>
        <div v-else><img class="flags" src='../assets/img/arco-flag.png' alt="arcobaleno">Lang= {{details.original_language}} </div>


        <div>{{details.vote_average}}</div>
        
        
    </div>
</template>

<script>
export default {
    name:"Film",
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
        flagImg() {
            if (this.details.original_language === 'it') {
                this.details.original_language = this.flagIta
            }
        }
    }

}
</script>

<style scoped lang="scss">
#movie {
    margin: 30px;
}
.flags {
    width: 20px;
}

</style>