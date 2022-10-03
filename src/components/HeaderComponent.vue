<template>
    <header>
    <h1>Boolflix</h1>
    <div>
      <input type="text" name="query" v-model="query" @keyup.enter="$emit('search' , query)">
      <button @click="$emit('search' , query)" >Vai!</button>
    </div>
    </header>
</template>

<script>
export default {
    name: 'HeaderComponent',
    data(){
        return{
            query: ''
        }
    }

}
</script>

<style lang="scss" scoped>
header{
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 10vh;
  background-color: black;
  padding: 10px;
  h1{
    font-size: 2rem;
    color: red;
  }
  input, button{
    height: 3vh;
    background-color:grey;
    border: 1px solid lightgray;
    color: white;
    margin: 0px 5px;
    padding: 0px 5px;
  }
}
</style>