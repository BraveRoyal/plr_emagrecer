<template>
  <div class="home">
    <center>
      <div class="all">
        <div class="text">
          <p class="header">FINALMENTE REVELADO:</p>
          <p class="title"> Está tentando <span class="green">emagrecer</span>, mas não consegue <b>ter resultados satisfatórios</b>? <br/>Descubra agora como <b>milhares de pessoas</b> estão perdendo peso e <span class="green">mudando de vida</span>!</p>
          <p class="second-title">Aumente o som e assista o video abaixo:</p>
        </div>
        <video-player  
          class="video-player-box"
          ref="videoPlayer"
          :options="playerOptions"
          :playsinline="true"
          customEventName="customstatechangedeventname">
        </video-player>
      </div>
    </center>
  </div>
</template>

<script lang="ts">
import 'video.js/dist/video-js.css'
import { videoPlayer } from 'vue-video-player'
import start from '@/assets/start.png'

export default {
  components: {
    videoPlayer
  },
  data() {
    return {
      playerOptions: {
        height: '360',
        sources: [{
          type: "video/mp4",
          src: "https://cdn.theguardian.tv/webM/2015/07/20/150716YesMen_synd_768k_vp8.webm"
        }],
        poster: start,
      }
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=BenchNine&display=swap');
.video-player-box{
  user-select: none;
}
.vjs-big-play-button{
  margin-top: 150px !important;
  margin-left: 260px !important;
}
.vjs-control-bar{
  visibility: hidden !important;
}
.all {
    font-family: 'BenchNine', sans-serif;
    width: 1000px;
}
.text{
  user-select: none;
  color: rgb(255, 255, 255);
  padding-top: 30px;
  width: 950px;
}
.green{
  color:#79f938;
  font-weight: bold;
}
.header{
  font-size: 50px;
}
.second-title{
  font-size: 25px;
  margin-bottom: 25px;
  width: 19%;
}
.title{
  font-size: 40px;
  margin-bottom: 25px;
}
@media only screen and (max-width: 1500px) {
  .all {
    font-family: 'BenchNine', sans-serif;
    width: 950px;
  }
  .text{
    user-select: none;
    color: rgb(255, 255, 255);
    padding-top: 30px;
    width: 100%;
  }
  .green{
    color:#79f938;
    font-weight: bold;
  }
  .header{
    font-size: 50px;
  }
  .second-title{
    font-size: 18px;
    margin-bottom: 25px;
    width: 14%;
  }
  .title{
    font-size: 40px;
    margin-bottom: 25px;
  }
}
@media only screen and (max-width: 1000px) {
  .all {
    font-family: 'BenchNine', sans-serif;
    width: 100vw;
  }
  .text{
    user-select: none;
    color: rgb(255, 255, 255);
    padding-top: 30px;
    width: 100%;
  }
  .green{
    color:#79f938;
    font-weight: bold;
  }
  .header{
    font-size: 20px;
  }
  .second-title{
    font-size: 10px;
    margin-bottom: 25px;
    width: 80%;
  }
  .title{
    font-size: 100%;
    margin-bottom: 25px;
  }
}
</style>
