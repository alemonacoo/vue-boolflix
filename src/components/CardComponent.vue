<template>
<div class="card">
        <div class="cardDescription">
            <p><strong>Title: </strong> {{title}}</p> 
            <p><strong>Original Title: </strong>{{originalTitle}}</p>
            <p><FlagComponent :language="language"/>
            </p> 
            <VoteComponent :vote="vote"/>
        </div>
        <PosterComponent class="poster" :image="image" :alt="title"/>
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
    margin: 10px;
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
    .cardDescription{
        padding: 10px;
    }
    .poster:hover{
          opacity: 0.2;
          transition: opacity .15s ease-in-out;
    }
}
</style>