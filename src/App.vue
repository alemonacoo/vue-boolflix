<template>
  <div id="app">
    <div>
      <input type="text" name="query" v-model="query" @keyup.enter="search()">
      <button @click="search()" >Vai!</button>
    </div>
    <div>
      <h2>Movies</h2>
      <MovieCard v-for="movie in movies" :key="movie.id" :movie="movie"/>
      <h2>Tv Series</h2>
      <TvSeriesCard v-for="tvSerie in tvSeries" :key="tvSerie.id" :tv="tvSerie"/>



    </div>
    
  </div>
</template>

<script>
import axios from 'axios';
import MovieCard from '@/components/movieCard.vue'
import TvSeriesCard from '@/components/tvSeriesCard.vue'



export default {
  name: 'App',
  data(){
    return{
      query: '',
      movies: [],
      tvSeries: [],
      apiUrl: 'https://api.themoviedb.org/3/',
      apiKey: 'ce51af1e7e90458d52e37ed3cac1c0a3'
    }
  },
  methods:{
    search(){
      axios.get(this.moviesLinkBuilder()).then((response)=>{
       this.movies = this.checkData(response);
       console.log(this.movies);
      })
      .catch(error => {
        console.log(error.message)
      });
      axios.get(this.tvLinkBuilder()).then((response)=>{
       this.tvSeries = this.checkData(response);
       console.log(this.tvSeries);
      })
      .catch(error => {
          console.log(error.message)
      });
      this.query = '';
    },
    moviesLinkBuilder(){
      return `${this.apiUrl}search/movie?api_key=${this.apiKey}&langage=it-IT&query=${this.query}&page=1&include_adult=false`;
    },
    tvLinkBuilder(){
      return `${this.apiUrl}search/tv?api_key=${this.apiKey}&langage=it-IT&query=${this.query}&page=1&include_adult=false`;
    },
    checkData(response){
      return response.status === 200 ? response.data.results : []; 
    }
  },
  components:{
    MovieCard,
    TvSeriesCard
  }
}
</script>

<style lang="scss">
#app {

}
</style>
