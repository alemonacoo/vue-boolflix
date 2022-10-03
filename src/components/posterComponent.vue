<template>
  <div>
    <img :src="getImage()" :alt="alt" @error="errorPoster($event)">
  </div>
</template>

<script>
export default {
    name: 'PosterComponent',
    props:{
        image: String,
        alt: String
    },
    methods:{
        getImage(){    
        const width = 500;
        return 'https://image.tmdb.org/t/p/w' + width + this.image;
        },
        errorPoster(event){
        event.target.src = 'https://www.metrorollerdoors.com.au/wp-content/uploads/2018/02/unavailable-image-300x225.jpg'
        }
    }


}
</script>

<style lang="scss" scoped>
// div{
//   position: absolute;
//   z-index: 2;
//   height: 100%;
//   width: 100%;
//   align-items: center;
//   display: flex;
//   justify-content: center;
// }
img{
    max-width: 180px;
    position: absolute;
    width: 100%;
}
// div:hover{
//   z-index: 0;
// }

</style>