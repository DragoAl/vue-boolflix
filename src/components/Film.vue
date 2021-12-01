<template>
    <div id="movie">
        <h3>{{details.original_title}}</h3>
        <h4>{{details.title}}</h4>
        <div>{{details.original_language}}</div>
        <div>{{details.vote_average}}</div>
        
    </div>
</template>

<script>
export default {
    name:"Film",
    props: {
        details: Object,
    }

}
</script>

<style scoped lang="scss">
#movie {
    margin: 30px;
}

</style>