<template>
  <div id="app">
    <div class="top">
     
      <div  class="bar">
       
     <ara  v-on:AramaIstegi="handleAra"></ara>
    
    </div>
    </div>
    <preview :gifs=gifs></preview>
    <p v-if="isLoading" class="load"> <img src="src/assets/loading.gif" ></p>
  </div>
</template>

<script>

import Ara from './components/Ara.vue'
import Preview from './components/Preview.vue'
export default {
  name: 'app',
  components:{ Ara, Preview },
  data(){
    return{
      isLoading: true,
      gifs: [],
      url:['src/assets/loading.gif'],
      urlload:['src/assets/giphyLogo.png'],
    }
   
  },
  
  methods: {
    handleAra(query){
        this.gifs = [];
        this.isLoading = true;
        fetch(`http://api.giphy.com/v1/gifs/search?q=${query}&api_key=dc6zaTOxFJmzC`)
       .then((res) => { return res.json() } )
       .then((res) => { 
       this.gifs = res.data;
       this.isLoading = false;
       } )
    }
  },
  created(){
    fetch('http://api.giphy.com/v1/gifs/trending?api_key=dc6zaTOxFJmzC')
    .then((res) => { return res.json() } )
    .then((res) => { 
      this.gifs = res.data;
      this.isLoading = false;
       } )
  }
  
}


</script>

<style>
html{
  background-color: #1a0e29;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

}
.top{
  background-color: #19adde;
  position: relative;
  top:0;
  left: 0px;
  width: 100%;
  padding-top: px;
  padding-bottom:5px;
  border-radius: 5px;
 
 }
   

.bar{
  margin:auto;
  padding:5px;
  
  width: 550px;
  
 
  }
  .ani{
    margin-top: 250px;
  transition: margin-top 1s;

  }
  .ani.yukari{
    margin-top:10px;
  }
  .logo{
     width: 560px;
     margin-top: 150px;
     transition: margin-top 1s;
   }
  .logo.yukari{
     margin-top:5px;
   }
 
  


</style>
