<template>
  <div id="app">
    <header>
      <input type="text" name="query" v-model="query" @keyup.enter="search()">
      <button @click="search()" >Vai!</button>
    </header>
    <div>
      <h2 v-if="movies.length > 0">Movies</h2>
      <CardComponent v-for="movie in movies" :key="movie.id"
      :title="movie.title"
      :originalTitle="movie.original_title"
      :vote="movie.vote_average"
      :language="movie.original_language"
      :image="movie.poster_path"
      />
      <h2 v-if="tvSeries.length > 0">Tv Series</h2>
      <CardComponent v-for="tv in tvSeries" :key="tv.id"
      :title="tv.name"
      :originalTitle="tv.original_name"
      :vote="tv.vote_average"
      :language="tv.original_language"
      :image="tv.poster_path"
      />
    </div>
    
  </div>
</template>

<script>
import axios from 'axios';
import CardComponent from '@/components/CardComponent.vue'



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
      return `${this.apiUrl}search/movie?api_key=${this.apiKey}&query=${this.query}&page=1&include_adult=false`;
    },
    tvLinkBuilder(){
      return `${this.apiUrl}search/tv?api_key=${this.apiKey}&query=${this.query}&page=1&include_adult=false`;
    },
    checkData(response){
      return response.status === 200 ? response.data.results : []; 
    }
  },
  components:{
    CardComponent
  }
}
</script>

<style lang="scss">
@import url(@/main.scss);
header{
  display: flex;
  align-items: center;
  height: 10vh;
  background-color: lightgray;
  input, button{
    height: 3vh;
  }
}
</style>
