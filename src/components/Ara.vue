<template>
    <div class="ara" >
        <img class="logo" v-bind:class="classObject" v-bind:src="url" />
        <input type="text" class="ani" v-bind:class="classObject" v-model="query" @keypress="handleAra(); toggle();  "  />
        <button type="button"  @click="handleAra(); toggle(); "   >Search</button>
    </div>
</template>

<script>
 export default {
    data(){
        return {
            
            query: '',
       classObject: {yukari: false},
    url:['src/assets/giphyLogo.png'],
        }
    },
    methods: {
        handleAra(){
            this.$emit('AramaIstegi', this.query);
        },
        toggle: function(){
        this.classObject.yukari = true;}
       
   
        
       
    },
    
   
    
}
</script>

<style>
    .ara input {
        padding: 10px 10px;
        border: 1px solid #CCC;
         border-radius: 5px;
         width: 400px;
    }
    .ara button{
        padding: 5px 15px;
        border: 1px solid #CCC;
        background-color: blueviolet;
        color:#FFF;
        font-size:16px;
        border-radius: 5px; 
    }
     .ani{
    margin-top: 50%;
    margin-bottom: 40px;
  transition: margin-top 1s;
    transition: margin-bottom 1s;


  }
  .ani.yukari{
    margin-top:5px;
    margin-bottom:5px;
  }
  
   .load{
     padding-left:44%;
   
   }
  
</style>