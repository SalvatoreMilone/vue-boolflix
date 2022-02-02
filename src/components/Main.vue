<template>
  <div>
    <InputRicerca 
    @SearchButton="MandaRicerca"
    />

    <div>

    </div>
   
  </div>
</template>



<script>

import axios from "axios"
import InputRicerca from './InputRicerca.vue'

export default {
  name: 'Main',
  components:{
    InputRicerca
  },

  data(){
    return{
      apiURL:"https://api.themoviedb.org/3/search/movie?api_key=",
      apiK:"8445a3b24421e8b2f034ace68840a37f",
      apiQuery:"&query=",
      searchQuery:""
    }
  },
  methods:{
    MandaRicerca(ricerca){
      this.searchQuery=ricerca;
      console.log(ricerca)
      axios
         .get(this.apiURL+this.apiK+this.apiQuery+this.searchQuery)
         .then( (risposta) => {
            console.log(risposta)
         })
         .catch(function (error) {
            console.log(error)
         })
    },
    cerca(){
      
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
