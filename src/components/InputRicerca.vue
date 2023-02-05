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
      <div class="container-background">
        <div class="img-overlay"></div>
        <div class="bg"></div>
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
  height: 150px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 100px;

}

.logo, .input-container{
  height: 70px;
  display: flex;
  align-items: center;
}
.logo img{
  height: 100%;

}

input{
  border: none;
  height: 30px;
}

input:nth-child(1){
  width:200px ;
  color: white;
  border-radius: 15px;
  padding: 10px;
  transition: all 300ms;
  margin-right: 5px;
  background-color: #171717;

  &:focus{
  background-color: black !important;
  width: 300px;
  box-shadow: 0px 3px 5px 0px #535353 inset, 0px 5px 5px 0px rgba(0, 0, 0, .3);
  }
}


input:nth-child(2){
  background-color: #db1927;
  border-radius:15px;
  width: 30px;
  padding:10px;
  transition: all 300ms; 

  &:hover{
  box-shadow: 0px 3px 5px 0px rgba(0, 0, 0, 0.4) inset;
  }
  &:focus{
  box-shadow: 0px 3px 10px 0px rgba(0, 0, 0, 0.7) inset;
     background-color: #90121a;
  }
}

.container-background{

  .bg{
    background-image: url("../assets/img/banner01.jpg");
    background-size:cover;
    background-repeat: no-repeat;
    position: absolute;
    left: 0;
    top:0;
    z-index: -1;
    width: 100%;
    height: 588px;
    opacity: .7;
  }

  .img-overlay{
    background: linear-gradient(0deg, rgba(23,23,23,1) 45%, rgba(23,23,23,0.6978992280505952) 70%, rgba(0,0,0,0) 100%);
    z-index: 0;
    height: 450px;
    width: 100%;
    position: absolute;
    top: calc(588px - 450px);
  }
}
@media screen and (max-width: 900px) {

  .container{
  height: 150px;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
  padding: 0 100px;

}

.logo, .input-container{
  height: 70px;
  display: flex;
  align-items: center;
}
.logo img{
  height: 100%;

}

input:nth-child(1){
  width:200px ;
  color: white;
  border-radius: 15px;
  padding: 10px;
  transition: all 300ms;
  margin-right: 5px;
  background-color: #171717;

  &:focus{
  background-color: black !important;
  width: 300px;
  box-shadow: 0px 3px 5px 0px #535353 inset, 0px 5px 5px 0px rgba(0, 0, 0, .3);
  }
}


input:nth-child(2){
  background-color: #db1927;
  border-radius:15px;
  width: 30px;
  padding:10px;
  transition: all 300ms; 

  &:hover{
  box-shadow: 0px 3px 5px 0px rgba(0, 0, 0, 0.4) inset;
  }
  &:focus{
  box-shadow: 0px 3px 10px 0px rgba(0, 0, 0, 0.7) inset;
     background-color: #90121a;
  }
}

.container-background{

  .bg{
    background-image: url("../assets/img/banner01.jpg");
    background-size:cover;
    background-repeat: no-repeat;
    position: absolute;
    left: 0;
    top:0;
    z-index: -1;
    width: 100%;
    height: 588px;
    opacity: .7;
  }

  .img-overlay{
    background: linear-gradient(0deg, rgba(23,23,23,1) 45%, rgba(23,23,23,0.6978992280505952) 70%, rgba(0,0,0,0) 100%);
    z-index: 0;
    height: 450px;
    width: 100%;
    position: absolute;
    top: calc(588px - 450px);
  }
}
}
</style>
