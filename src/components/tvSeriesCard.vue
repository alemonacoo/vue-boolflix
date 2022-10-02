<template>
    <div>
        <p>Title: {{tv.name}}</p> 
        <p>Original Title: {{tv.original_name}}</p> 
        <p>Language: {{tv.original_language}}</p>
        <p>Vote: {{tv.vote_average}}</p> 
    </div>
</template>

<script>
export default {
    name: 'TvSeriesCard',
    props:{
        tv: Object,
    }
}
</script>

<style lang="scss" scoped>
div{
    margin: 50px 0px;
}


</style>