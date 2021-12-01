<template>
    <div id="tvseries">
        <h3>{{details.original_name}}</h3>
        <h4>{{details.name}}</h4>
        
        <div v-if="details.original_language === 'it' "><img src= '../assets/img/ita-flag.png' alt="italy"></div>
        <div v-else-if="details.original_language === 'en' "><img src= '../assets/img/greatbritain-flag.png' alt="greatbritain"></div>
        <div v-else>`Bandiera non disponibile: Lang= {{details.original_language}}` </div>


        <div>{{details.vote_average}}</div>
        
        
    </div>
</template>

<script>
export default {
    name:"TvSeries",
    data() {
        return {
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
img {
    width: 20px;
}

</style>