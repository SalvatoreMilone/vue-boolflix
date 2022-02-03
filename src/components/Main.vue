<template>
  <div>
    <InputRicerca 
    @SearchButton="MandaRicercaFilm"
    />
    <div class="container">
      <div>
        <Filmcard
          v-for="(element, index) in filmArray"
          :key="index"
          :film="filmArray"
          :index="index"
          :elemento="element"
        />
        <Seriecard
        v-for="(element, index) in serieArray"
          :key="index+20"
          :serie="serieArray"
          :index="index"
          :elemento="element"
        />
      </div>
    </div>
   
  </div>
</template>



<script>

import axios from "axios"
import InputRicerca from './InputRicerca.vue'
import Filmcard from './Filmcard.vue'
import Seriecard from './Seriecard.vue'

export default {
  name: 'Main',
  components:{
    InputRicerca,
    Filmcard,
    Seriecard,
  },
  data(){
    return{
      apiURLMovie:"https://api.themoviedb.org/3/search/movie?",
      apiURLSerie:"https://api.themoviedb.org/3/search/tv?",
      searchQuery:"",
      filmArray:[],
      serieArray:[],
    }
  },
  methods:{
    MandaRicercaFilm(ricerca){
      this.searchQuery=ricerca;
      axios
         .get(this.apiURLMovie, {
           params:{
             api_key:"8445a3b24421e8b2f034ace68840a37f",
             query:this.searchQuery,
           },
         })
         .then( (risposta) => {
            this.filmArray = risposta.data.results;
            this.MandaRicercaSerie()
         })
         .catch(function (error) {
            console.log(error)
         })
    },
    MandaRicercaSerie(){
      axios
         .get(this.apiURLSerie, {
             params:{
             api_key:"8445a3b24421e8b2f034ace68840a37f",
             query:this.searchQuery,
           },
         })
         .then( (risposta) => {
            this.serieArray = risposta.data.results;
         })
         .catch(function (error) {
            console.log(error)
         })
    },
  },  
   mounted() {
     this.MandaRicercaFilm("vento")
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.container > div{
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  align-items:flex-start ;

}

.container{
  margin: 0 auto;
  width: 92%;
  margin-top: 50px;
}
</style>
