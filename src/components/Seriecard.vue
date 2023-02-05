<template>
  <div>
    <Tilt>
      <div class="container">
        <div class="img-container">
          <img :src="imglink + serie[index].poster_path" alt="cover not found">
        </div>
        <div class="content">
          <div class="title">{{serie[index].name}}</div>
          <div class="original-title">{{serie[index].original_name}}</div>

          <div class="lang-container">
            <img :src="require(`../assets/img/${getFlag(serie[index].original_language)}.png`)" alt="?">
            <span class="lang">{{serie[index].original_language}}</span>
          </div>

          <div class="vote-container">

            <div v-for="(element, i) in Math.round((serie[index].vote_average)/2)" :key="i" class="vote true">
              <svg height="25" width="23" class="star">
                <polygon points="9.9, 1.1, 3.3, 21.78, 19.8, 8.58, 0, 8.58, 16.5, 21.78" style="fill-rule:nonzero;"/>
              </svg>
            </div>

            <div v-for="(element, i) in (5 - (Math.round((serie[index].vote_average)/2)))" :key="i+5">
              <svg height="25" width="23" class="star">
                <polygon points="9.9, 1.1, 3.3, 21.78, 19.8, 8.58, 0, 8.58, 16.5, 21.78" style="fill-rule:nonzero;"/>
              </svg>
            </div>

          </div>

          <div class="overview">
            {{serie[index].overview}}
          </div>

        </div>
      </div>
    </Tilt>
  </div>
</template>



<script>

import Tilt from 'vanilla-tilt-vue'

export default {
  name: 'Seriecard',
  components:{
    Tilt,
  },
  props:{
    serie: Array,
    index: Number,
  },
  data(){
    return{
      imglink:"https://image.tmdb.org/t/p/w300/",
      voteAbbr: "vote-",
    }
  },
  methods:{
    getFlag: function(flag){
      if(flag == "it"){
        return "it"
      }else if(flag == "en"){
        return "en"
      }else{
        return "others"
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.container{
  margin: 10px;
  background-color: #333;
  font-weight:400;
  width: 250px;
  height: 450px;
  border-radius: 10px;
  color: white;
  position: relative;
  box-shadow: 0px 10px 15px -5px black;

  &:hover{
    box-shadow: 0px 10px 15px 5px rgba(0, 0, 0, .6);
  }

  &:hover > .content{
    opacity: 1;
  }
  &:hover > .img-container img{
    opacity: .3  ;
    filter: blur(10px);
  }
}

.content{
  height: 409px;
  opacity: 0;
  position: absolute;
  top: 10px;
  left: 10px;
  transition: all 300ms;
  overflow: hidden;
}


.overview{
  overflow: hidden;
  white-space: pre-wrap;
  word-break:normal;
}

.original-title{
  margin: 10px 0;
  color: #999;
  font-size: .8rem;
  font-weight:300;
}

.img-container{
  width: 250px;
  height: 450px;
  overflow: hidden;
  background-color: #222;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  line-height: 450px;
  border-radius: 5px;
  margin-bottom: 10px;

  img{
    height: 450px;
    transition: all 300ms;
  }
}


.vote-container{
  display: flex;
  margin: 5px 0;
}

.vote.true{
  fill: rgb(255, 204, 0);
}

.lang-container{
  display: flex;
  align-items: center;
  width: fit-content;

  img{
    width: 30px;
  }

  & .lang{
    display: none;
    margin-left: 10px;
  }

  &:hover .lang{
    display: block;
  }
}
@media screen and (max-width: 900px) {
  .container{
    display: block;
    margin: 10px;
    background-color: #333;
    font-weight:400;
    width: 150px;
    height: 250px;
    border-radius: 10px;
    color: white;
    position: relative;
    box-shadow: 0px 10px 15px -5px black;

    .img-container{
      width: 150px;
      height: 250px;
      overflow: hidden;
      background-color: #222;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      line-height: 250px;
      border-radius: 5px;
      margin-bottom: 10px;

      img{
        height: 250px;
        transition: all 300ms;
      }
    }
  }
    .content{
    height: 230px;
    opacity: 0;
    position: absolute;
    top: 10px;
    left: 10px;
    transition: all 300ms;
    overflow-x: hidden;
    overflow-y: auto;
  }
}
</style>
