<template>
  <div>

   <input type="text"
   v-model="ricerca"
   v-on:keyup.enter="$emit('SearchButton', ricerca), ClearSearchButton()">

   <input type="submit" value="search"
   @click="$emit('SearchButton', ricerca), ClearSearchButton()">

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

</style>
