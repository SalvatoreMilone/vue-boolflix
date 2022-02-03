<template>
  <div>
    <div class="container">

      <div class="logo">
        <img src="../assets/img/logo.png">
      </div>

      <div class="input-container">
        <input type="text"
        placeholder="Search the perfect movie"
        v-model="ricerca"
        v-on:keyup.enter="$emit('SearchButton', ricerca), ClearSearchButton()">

        <input type="submit" value=""
        @click="$emit('SearchButton', ricerca), ClearSearchButton()">
      </div>

    </div>
  </div>
</template>



<script>
export default {
  name: 'InputRicerca',
  components:{
      
  },

  data(){
    return{
      ricerca:"",
    }
  },
  methods:{
    ClearSearchButton(){
      this.ricerca = ""
    }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.container{
  background-color: black;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 20px;
}

.logo, .input-container{
  height: 50px;
  display: flex;
  align-items: center;
}
.logo img{
  height: 90%;
}

input{
  border: none;
  background-color: #777;
  height: 30px;
}

input:nth-child(1){
  width:200px ;
  color: white;
  border-radius: 15px;
  padding: 10px;
  transition: all 300ms;
  margin-right: 5px;

  &:focus{
  background-color: #555 !important;
  width: 300px;
  box-shadow: 0px 3px 5px 0px rgba(255, 252, 252, .4) inset;
  background-color: #888 !important;
  }
}


input:nth-child(2){
  border-radius:15px;
  width: 30px;
  padding:10px;

  &:hover{
  box-shadow: 0px 3px 5px 0px rgba(255, 252, 252, .4) inset;
  }
  &:focus{
  box-shadow: 0px 3px 10px 0px rgba(255, 252, 252, .7) inset;
   background-color: #888 !important;
  }
}

</style>
