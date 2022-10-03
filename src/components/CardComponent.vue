<template>
<div class="card">
        <p><strong>Title: </strong> {{title}}</p> 
        <p><strong>Original Title: </strong>{{originalTitle}}</p>
        <p><FlagComponent :language="language"/>
        </p> 
        <VoteComponent :vote="vote"/>
        <PosterComponent :image="image" :alt="title"/>
</div>
</template>

<script>
import FlagComponent from '@/components/flagComponent.vue';
import PosterComponent from '@/components/posterComponent.vue';
import VoteComponent from '@/components/voteComponent.vue';


export default {
    name: 'CardComponent',
    props:{
        title: String,
        originalTitle: String,
        language: String,
        vote: Number,
        image: String
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
    margin: 10px;
    padding: 10px;
    flex-shrink: 0;
    flex-direction: column;
    display: flex;
    overflow-x: auto;
    background-color: black;
    width: 200px;
    height: 320px;
    position: relative;
    z-index: 1;
    font-size: 0.9rem;
    border-radius: 5px;

}
</style>