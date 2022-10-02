<template>
    <div class="card">
        <p>Title: {{tv.name}}</p> 
        <p>Original Title: {{tv.original_name}}</p> 
        <p>Language: 
        <FlagComponent :language="tv.original_language"/>
        </p> 
        <VoteComponent :vote="tv.vote_average"/>
        <PosterComponent :image="tv.poster_path" :alt="tv.title"/>

    </div>
</template>

<script>

import FlagComponent from '@/components/flagComponent.vue';
import PosterComponent from '@/components/posterComponent.vue';
import VoteComponent from '@/components/voteComponent.vue';


export default {
    name: 'TvSeriesCard',
    props:{
        tv: Object,
    },components:{
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