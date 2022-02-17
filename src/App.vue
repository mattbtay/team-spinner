<template>
  <Spinner :users="users" />
</template>

<script>
import Spinner from './components/Spinner.vue'

export default {
  name: 'App',
  components: {
    Spinner
  },
  data(){
    return {
      users: [
        {name: 'matt', color: '#4e79a7'}, 
        {name: 'sofia', color: '#f28e2c'}, 
        {name: 'andres', color: '#e15759'}, 
        {name: 'Alan', color: '#59a14f'},
        {name: 'Amit', color: '#000'},
        {name: 'Sunitha', color: '#6666'},
        ],
        
    }
  }
}
</script>

<style>
body {
  margin:0;
  padding:0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height:100vh;
}
</style>
