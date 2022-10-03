<template>
<div class="card">
        <p>Title: {{title}}</p> 
        <p>Original Title: {{originalTitle}}</p>
        <p>Language: 
        <FlagComponent :language="language"/>
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
    margin: 20px 0px;
}
</style>