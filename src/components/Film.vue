<template>
    <div id="movie"  @click="$emit('clickFilm',idFilm)" >
        
        <img class="poster" :src="baseUrl + sizeImg + posterPath" :alt= details.original_title>
        <div class="infocards">
            <h4>Titolo : <span>{{details.original_title}}</span></h4>
            <h4>Titolo Originale : <span>{{details.title}}</span></h4>
            
            <div v-if="details.original_language === 'it' "><h4>Lingua Originale:</h4> <img class="flags" src= '../assets/img/ita-flag.png' alt="italy"></div>
            <div v-else-if="details.original_language === 'en' "><h4>Lingua Originale:</h4><img class="flags" src= '../assets/img/greatbritain-flag.png' alt="greatbritain"></div>
            <div v-else><h4>Lingua Originale:</h4><img class="flags" src='../assets/img/arco-flag.png' alt="arcobaleno">Lang= {{details.original_language}} </div>

            <!-- <div>{{voteBase5}}</div> -->
            <div class="voto"> 
                <h4>Voto:</h4>
                <i v-for="o in voteBase5 " :key="'up' +o" class="fas fa-star full-star"></i>
                <i v-for="y in 5 - voteBase5 " :key="'down'+y" class="far fa-star empty-star"></i>
            </div>
            <div class="overview">
                <h4>Overview: </h4>
                <p>{{details.overview}} </p>
            </div>
            
          
        </div>
        <div class="cast" v-if="activeMovie === true && idActive === idFilm ">
            <div  v-for="actor, i in castArray.slice(0, 5) " :key="'actor' + i">{{actor.name}}</div>

        </div>
    </div>
</template>

<script>
export default {
    name:"Film",
    data() {
        return {
            baseUrl: 'https://image.tmdb.org/t/p/',
            sizeImg:'w342/',
            posterPath: this.details.poster_path,
            originalVoteAvg: this.details.vote_average,
            voteBase5:'' ,
            idFilm: this.details.id,
            
        }
    },
    props: {
        details: Object,
        castArray:Array,
        activeMovie: Boolean,
        idActive: Number
    },
    created() {
        this.vote1to5()
    },

    methods : {
        vote1to5() {
            return this.voteBase5 =Math.ceil(this.originalVoteAvg / 2)
        }
    }
}
</script>

<style scoped lang="scss">
#movie {
    margin: 30px;
    position: relative;
    cursor: pointer;
    
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

.flags {
    width: 20px;
    transform: translate(40%, 25%);

   
}

</style>