<template>
<div>
        <p>Title: {{movie.title}}</p> 
        <p>Original Title: {{movie.original_title}}</p> 
        <p>Language: {{movie.original_language}}</p>
        <p>Vote: {{movie.vote_average}}</p> 
</div>
</template>

<script>
export default {
    name: 'MovieCard',
    props:{
        movie: Object,
    }
}
</script>

<style lang="scss" scoped>
div{
    margin: 50px 0px;
}
</style>