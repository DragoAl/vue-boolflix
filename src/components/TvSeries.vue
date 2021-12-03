<template>
    <div id="tvseries" @click="$emit('clickTv',idTv)">
        <img class="poster" :src="baseUrl + sizeImg + posterPath" :alt= details.original_title>
        <div class="infocards">
            <h4>Titolo : <span>{{details.original_name}}</span></h4>
            <h4>Titolo Originale : <span>{{details.name}}</span></h4>
            
            <div v-if="details.original_language === 'it' "><h4>Lingua Originale:</h4> <img class="flags" src= '../assets/img/ita-flag.png' alt="italy"></div>
            <div v-else-if="details.original_language === 'en' "><h4>Lingua Originale:</h4><img class="flags" src= '../assets/img/greatbritain-flag.png' alt="greatbritain"></div>
            <div v-else><h4>Lingua Originale:</h4><img class="flags" src='../assets/img/arco-flag.png' alt="arcobaleno">Lang= {{details.original_language}} </div>

            <!-- <div >{{voteBase5}} </div> -->
            <div class="voto">
                <h4>Voto:</h4>
                <i v-for="n in voteBase5 " :key="'full'+n" class="fas fa-star full-star"> </i>
                <i v-for="y in 5 - voteBase5 " :key="'empty'+y" class="far fa-star empty-star"></i>
            </div>
            
            <div class="overview">
                <h4>Overview: </h4>
                <p>{{details.overview}} </p>
            </div>
            
            <div class="cast" v-if="activeTv === true && idActive === idTv ">
                <h4>Cast</h4>
                <div  v-for="actor, i in castArray.slice(0, 5) " :key="'actor' + i">{{actor.name}}</div>
                
                <h4>Generi</h4>
                <div  v-for="genre, i in listGenreTv.slice(0, 5) " :key="'genre' + i">{{genre.name}}</div>


            </div>
           
        </div>
        
        
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
            idTv: this.details.id,

            
        }
    },

    props: {
        details: Object,
        castArray:Array,
        activeTv: Boolean,
        idActive: Number,
        listGenreTv: Array
    },

    created() {
        this.vote1to5()
    },
    computed: {
        
    },

    methods : {
        vote1to5() {
            return this.voteBase5 =Math.floor(this.originalVoteAvg / 2)
        },
    }

}
</script>

<style scoped lang="scss">
#tvseries {
    margin: 30px; 
    position: relative;
    
    &:hover .infocards  {
        display: block;
    }

    .infocards {
        position: absolute;
        top: 0;
        left: 0;
        color: white;
        border: 1px solid white;
        background-color: black;
        width: 100%;
        height: 100%;
        display: none;
        padding: 0 15px;
        overflow: scroll;

    }

    .poster {
        border: 1px solid white;
    }
}
h4 {
    display: inline-block;
    margin-top: 10px;
}

.voto {
    margin-top: 10px;
}
.overview {
    margin-top:10px ;
    p {
        height: 40vh;
        overflow: scroll;
    }
}

.cast {
    overflow: scroll;
}

.flags{
    width: 20px;
    transform: translate(40%, 25%);

}


</style>