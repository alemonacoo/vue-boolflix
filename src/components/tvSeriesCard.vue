<template>
    <div class="card">
        <p>Title: {{tv.name}}</p> 
        <p>Original Title: {{tv.original_name}}</p> 
        <p>Language: 
        <FlagComponent :language="tv.original_language"/>
        </p> 
        <p>Vote: {{tv.vote_average}}</p> 
    </div>
</template>

<script>

import FlagComponent from '@/components/flagComponent.vue';

export default {
    name: 'TvSeriesCard',
    props:{
        tv: Object,
    },components:{
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