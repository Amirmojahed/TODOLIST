<template>
  <div class="main">
   
    <Addlist /> 
      
  </div>
</template>

<script>
import Addlist from './components/Addlist.vue'
export default {
  name: 'App',
  components: {Addlist}
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.main{
  width: 80%;
  background-color: rgba(38, 0, 255, 0.144);
  margin: auto;
  border: 1px solid rgb(226, 226, 226);
  box-shadow: 1px 1px 40px -10px #31505f30, 0px 1px 2px 0px #31505f30;
  border-radius: 20px 20px;
  padding: 20px;
}


</style>
