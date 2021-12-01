<template>
    <div id="movie">
        <h3>{{details.original_title}}</h3>
        <h4>{{details.title}}</h4>
        
        <div v-if="details.original_language === 'it' "><img src= '../assets/img/ita-flag.png' alt="italy"></div>
        <div v-else-if="details.original_language === 'en' "><img src= '../assets/img/greatbritain-flag.png' alt="greatbritain"></div>
        <div v-else>`Bandiera non disponibile: Lang= {{details.original_language}}` </div>


        <div>{{details.vote_average}}</div>
        
        
    </div>
</template>

<script>
export default {
    name:"Film",
    data() {
        return {
            flagIta: '../assets/img/ita-flag.png'
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
img {
    width: 20px;
}

</style>