<template>
  <div>
    <font-awesome-icon icon="fa-regular fa-star" />
    <font-awesome-icon icon="fa-solid fa-star" />

    {{getOneToFive(vote)}}
  </div>
</template>

<script>
import Vue from 'vue'
import { library } from '@fortawesome/fontawesome-svg-core'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faStar as faStarSolid } from '@fortawesome/free-regular-svg-icons'
import { faStar as faStarRegular} from '@fortawesome/free-solid-svg-icons'
library.add(faStarSolid, faStarRegular);
Vue.component('font-awesome-icon', FontAwesomeIcon)
Vue.config.productionTip = false


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