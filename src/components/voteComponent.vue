<template>
  <div>
    <FontAwesomeIcon icon="fa-solid fa-star" />
    {{getOneToFive(vote)}}
  </div>
</template>

<script>
export default {
    name: 'VoteComponent',
    props:{
        vote: Number,
    }, 
    methods:{
        getOneToFive(n){
            return Math.ceil(n/2);
        }
    }

}
</script>

<style>

</style>