<template>
  <div class="StarsContainer">
    <div>
    <font-awesome-icon v-for="fullStar in getStars(vote)" 
    :key="fullStar" icon="fa-solid fa-star" />
    </div>
    <div>  
      <font-awesome-icon v-for="emptyStar in (MAX_STARS - getStars(vote))" 
      :key="emptyStar" icon="fa-regular fa-star" />
    </div>
  </div>
</template>

<script>
//Importing fontawesome star icons
import Vue from 'vue'
import { library } from '@fortawesome/fontawesome-svg-core'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faStar as faStarSolid } from '@fortawesome/free-regular-svg-icons'
import { faStar as faStarRegular} from '@fortawesome/free-solid-svg-icons'
library.add(faStarSolid, faStarRegular);
Vue.component('font-awesome-icon', FontAwesomeIcon)
Vue.config.productionTip = false

//Numer of Stars
const MAX_STARS = 5;


export default {
    name: 'VoteComponent',
    props:{
        vote: Number,
    }, 
    data(){
      return{
        MAX_STARS,
      }
    },
    methods:{
        getStars(n){
          if(n === 0){
            return 1;
          }
            return Math.ceil(n / (10 / MAX_STARS));
        }
    }

}
</script>

<style lang="scss" scoper>
.StarsContainer{
  display: flex;
}

</style>