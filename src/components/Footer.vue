<template>
  <div>
    <div class="container">Made with <span>&#x2764;</span></div>
  </div>
</template>



<script>
export default {
  name: 'Footer',
  components:{
      
  },

  data(){
    return{
     
    }
  },
  methods:{
    
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.container{
  background: linear-gradient(0deg, rgba(0,0,0,1) 0%, rgba(0,0,0,0.4) 40%, rgba(0,0,0,0) 100%);
  color: white;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;

  span{
    color: red;
  }
}
</style>
