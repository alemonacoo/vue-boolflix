<template>
    <header>
      <input type="text" name="query" v-model="query" @keyup.enter="$emit('search' , query)">
      <button @click="$emit('search' , query)" >Vai!</button>
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

<style>

</style>