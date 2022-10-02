<template>
<div class="card">
        <p>Title: {{movie.title}}</p> 
        <p>Original Title: {{movie.original_title}}</p>
        <p>Language: 
        <FlagComponent :language="movie.original_language"/>
        </p> 
        <p>Vote: {{movie.vote_average}}</p> 
</div>
</template>


<script>

import FlagComponent from '@/components/flagComponent.vue';

export default {
    name: 'MovieCard',
    props:{
        movie: Object,
    }, 
    components:{
        FlagComponent
    }
}
</script>

<style lang="scss" scoped>
.card{
    border: 1px solid black;
    margin: 20px 0px;
}
</style>