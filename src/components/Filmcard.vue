<template>
  <div>
    <Tilt>
      <div class="container">
        <div class="img-container">
          <img :src="imglink + film[index].poster_path" alt="cover not found">
        </div>
        <div class="content">

          <div class="title">{{film[index].title}}</div>
          <div class="original-title">{{film[index].original_title}}</div>

          <div v-if="(film[index].original_language) == 'it'">
            <svg width="25px" viewBox="0 0 3 2">
              <rect width="1" height="2" fill="#009246"></rect>
              <rect width="1" height="2" x="1" fill="#fff"></rect>
              <rect width="1" height="2" x="2" fill="#ce2b37"></rect>
            </svg>
          </div>
          <div v-else-if="(film[index].original_language) == 'en'">
            <svg width="25px" viewBox="0 0 7410 3900">
              <rect xmlns="http://www.w3.org/2000/svg" width="7410" height="3900" fill="#b22234"/>
              <path xmlns="http://www.w3.org/2000/svg" d="M0,450H7410m0,600H0m0,600H7410m0,600H0m0,600H7410m0,600H0" stroke="#fff" stroke-width="300"/>
              <rect xmlns="http://www.w3.org/2000/svg" width="2964" height="2100" fill="#3c3b6e"/>
            </svg>
          </div>
          <div v-else>
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 64 64" enable-background="new 0 0 64 64" width="23px" style="stroke: white;fill: white;" >
              <path d="m32 2c-16.541 0-30 13.459-30 30 0 16.543 13.459 30 30 30 16.542 0 30-13.457 30-30 0-16.541-13.457-30-30-30m20.047 46.204c-1.195-1.083-2.463-2.058-3.793-2.923 1.674-3.385 2.703-7.074 3.012-10.859h6.41c-.487 5.191-2.518 9.941-5.629 13.782m-45.721-13.782h6.297c.311 3.803 1.35 7.514 3.039 10.914-1.299.852-2.539 1.809-3.709 2.868-3.111-3.841-5.142-8.591-5.627-13.782m5.627-18.625c1.17 1.061 2.41 2.018 3.709 2.867-1.783 3.588-2.842 7.52-3.084 11.547h-6.305c.375-5.438 2.444-10.418 5.68-14.414m17.942-6.238v9.648c-2.926-.234-5.746-.955-8.367-2.125 2.189-3.07 5.04-5.654 8.367-7.523m0 13.869v6.783h-13.098c.234-3.359 1.127-6.57 2.557-9.488 3.283 1.531 6.839 2.452 10.541 2.705m0 10.994v6.15c-3.713.255-7.281 1.181-10.574 2.723-1.326-2.732-2.182-5.727-2.473-8.873h13.047m0 10.373v9.668c-3.363-1.867-6.225-4.447-8.412-7.523 2.634-1.182 5.468-1.911 8.412-2.145m4.21 9.58v-9.58c2.895.23 5.682.938 8.277 2.084-2.167 3.05-4.987 5.623-8.277 7.496m0-13.803v-6.15h12.934c-.297 3.111-1.156 6.088-2.488 8.812-3.256-1.505-6.78-2.41-10.446-2.662m0-10.361v-6.783c3.666-.25 7.193-1.156 10.451-2.662 1.418 2.906 2.301 6.102 2.535 9.445h-12.986m0-11.004v-9.584c3.293 1.872 6.113 4.445 8.283 7.496-2.597 1.149-5.386 1.856-8.283 2.088m10.428-6.241c-1.984-2.404-4.328-4.471-6.918-6.138 4.357.971 8.301 3.048 11.523 5.92-.953.857-1.961 1.637-3.016 2.333-.495-.727-1.026-1.433-1.589-2.115m-25.178.001c-.549.666-1.068 1.354-1.555 2.063-1.027-.684-2.008-1.445-2.939-2.281 3.182-2.835 7.064-4.896 11.355-5.883-2.568 1.659-4.89 3.713-6.861 6.101m-1.554 36.004c.408.594.838 1.174 1.291 1.738 2.021 2.521 4.439 4.689 7.129 6.428-4.291-.986-8.178-3.048-11.359-5.884.931-.837 1.913-1.599 2.939-2.282m26.773 2.013c.547-.666 1.064-1.355 1.551-2.064 1.053.696 2.061 1.476 3.014 2.333-3.223 2.872-7.166 4.948-11.523 5.92 2.609-1.679 4.964-3.763 6.958-6.189m6.737-20.773c-.24-4.008-1.289-7.92-3.057-11.492 1.33-.864 2.598-1.839 3.793-2.922 3.238 3.996 5.305 8.977 5.68 14.414h-6.416"/>
              </svg>
          </div>
          <div class="vote" :id="voteAbbr+Math.round((film[index].vote_average)/2)">

          <div v-for="(element, i) in 5" :key="i" class="vote">
            <svg height="25" width="23" class="star">
              <polygon points="9.9, 1.1, 3.3, 21.78, 19.8, 8.58, 0, 8.58, 16.5, 21.78" style="fill-rule:nonzero;"/>
            </svg>
          </div>

          </div>

          <div class="overview">
            {{film[index].overview}}
          </div>
        </div>
      </div>
    </Tilt>
  </div>
</template>

<script>

import Tilt from 'vanilla-tilt-vue'

export default {
  name: 'Filmcard',
  components:{
    Tilt,
  },
  props:{
    film: Array,
    index: Number,
    elemento: Object,
  },
  data(){
    return{
      imglink:"https://image.tmdb.org/t/p/w300/",
      voteAbbr: "vote-",
    }
  },
  methods:{

  },
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
    opacity: .3;
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
}

img{
  height: 450px;
  transition: all 300ms;
}

#vote-1 div:nth-child(1){
  fill: rgb(255, 204, 0);
}
#vote-2 div:nth-child(1),#vote-2 div:nth-child(2){
  fill: rgb(255, 204, 0);
}
#vote-3 div:nth-child(1),#vote-3 div:nth-child(2), #vote-3 div:nth-child(3){
  fill: rgb(255, 204, 0);
}
#vote-4 div:nth-child(1),#vote-4 div:nth-child(2), #vote-4 div:nth-child(3), #vote-4 div:nth-child(4){
  fill: rgb(255, 204, 0);
}
#vote-5 div:nth-child(1),#vote-5 div:nth-child(2), #vote-5 div:nth-child(3), #vote-5 div:nth-child(4), #vote-5 div:nth-child(5){
  fill: rgb(255, 204, 0);
}

.vote{
  display: flex;
  margin: 5px 0;
}
</style>