<template>

    <textarea style="height:150px; width:400px; margin-top:15%;" v-if="!ready" v-model="users" />
    <button style="margin-left:10px; display:block; margin:0 auto; background:black; color:#fff; padding:15px 24px; border:none;" v-if="!ready" @click="ready = true">Let Roman Choose</button>

  <Spinner v-if="ready" :users="usersList()" />
</template>

<script>
import Spinner from './components/Spinner.vue'
var randomColor = require('randomcolor');

export default {
  name: 'App',
  components: {
    Spinner
  },
  data(){
    return {
      users:'',
      ready: false,
              
    }
  },
  methods: {
    usersList(){
      var list = [];
      var listArray = this.users.split(',');
      for (var i = 0; i<listArray.length; i++){
        var person = listArray[i];
        list.push({name: person, color: randomColor()})
      }
    return list;
  },
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
