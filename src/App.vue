<template>
  <div id="app">
    <HeaderComponent @search="search"/>
    <div class="cards-container">
      <h2 v-if="movies.length > 0">Movies</h2>
      <div v-else>
        <h2>Benvenuto su Boolflix!</h2>
        <p>Per cominciare, cerca un film o una Serie Tv nella barra di ricerca</p>
        <p>- by A.M.</p>
      </div>
      <div class="movies-container">
      <CardComponent v-for="movie in movies" :key="movie.id"
      :title="movie.title"
      :originalTitle="movie.original_title"
      :vote="movie.vote_average"
      :language="movie.original_language"
      :image="movie.poster_path"
      :overview="movie.overview"
      />
      </div>
      <h2 v-if="tvSeries.length > 0">Tv Series</h2>
      <div class="tvseries-container">
      <CardComponent v-for="tv in tvSeries" :key="tv.id"
      :title="tv.name"
      :originalTitle="tv.original_name"
      :vote="tv.vote_average"
      :language="tv.original_language"
      :image="tv.poster_path"
      :overview="tv.overview"
      />
      </div>
    </div>
    
  </div>
</template>

<script>
import axios from 'axios';
import HeaderComponent from '@/components/HeaderComponent.vue'
import CardComponent from '@/components/CardComponent.vue'



export default {
  name: 'App',
  data(){
    return{
      movies: [],
      tvSeries: [],
      apiUrl: 'https://api.themoviedb.org/3/',
      apiKey: 'ce51af1e7e90458d52e37ed3cac1c0a3'
    }
  },
  methods:{
    search(textToSearch){
      axios.get(this.moviesLinkBuilder(textToSearch)).then((response)=>{
       this.movies = this.checkData(response);
       console.log(this.movies);
      })
      .catch(error => {
        console.log(error.message)
      });
      axios.get(this.tvLinkBuilder(textToSearch)).then((response)=>{
       this.tvSeries = this.checkData(response);
       console.log(this.tvSeries);
      })
      .catch(error => {
          console.log(error.message)
      });
      this.sortByPopularity();
      this.query = '';
    },
    moviesLinkBuilder(textToBuild){
      return `${this.apiUrl}search/movie?api_key=${this.apiKey}&query=${textToBuild}&page=1&include_adult=false`;
    },
    tvLinkBuilder(textToBuild){
      return `${this.apiUrl}search/tv?api_key=${this.apiKey}&query=${textToBuild}&page=1&include_adult=false`;
    },
    checkData(response){
      return response.status === 200 ? response.data.results : []; 
    },
    sortByPopularity(){
      this.movies.sort((a, b) => a.popularity - b.popularity);
      this.tvSeries.sort((a, b) => a.popularity - b.popularity)
    }
  },
  components:{
    HeaderComponent,
    CardComponent
  }
}
</script>

<style lang="scss" scoped>
@import url(@/main.scss);
    .cards-container{
    display: flex;
    flex-direction: column;
    row-gap: 10px;
    padding: 20px 40px;
    min-height: 90vh;
    background-color: #2b2b2b;
    color: white;
    h2{
      margin-top:10px
    }
    .movies-container,
    .tvseries-container{
      display: flex;
      overflow-x: auto;
    }
    }
</style>
