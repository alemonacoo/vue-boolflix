<template>
<div class="card">
        <p>Title: {{movie.title}}</p> 
        <p>Original Title: {{movie.original_title}}</p>
        <p>Language: 
        <FlagComponent :language="movie.original_language"/>
        </p> 
        <VoteComponent :vote="movie.vote_average"/>
        <PosterComponent :image="movie.poster_path" :alt="movie.title"/>
</div>
</template>


<script>

import FlagComponent from '@/components/flagComponent.vue';
import PosterComponent from '@/components/posterComponent.vue';
import VoteComponent from '@/components/voteComponent.vue';

export default {
    name: 'MovieCard',
    props:{
        movie: Object,
    }, 
    components:{
        FlagComponent,
        PosterComponent,
        VoteComponent
    }
}
</script>

<style lang="scss" scoped>
.card{
    border: 1px solid black;
    margin: 20px 0px;
}
</style>