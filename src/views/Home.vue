<template>
  <div class="home">
    <center>
      <div class="all">
        <div class="text">
          <p class="header">FINALMENTE REVELADO:</p>
          <p class="title"> Está tentando <span class="green">emagrecer</span>, mas não consegue <b>ter resultados satisfatórios</b>? <br/>Descubra agora como <b>milhares de pessoas</b> estão perdendo peso e <span class="green">mudando de vida</span>!</p>
          <p class="second-title">Aumente o som e assista o video abaixo:</p>
        </div>
        <div class="player" @touchstart="videoClick">
          <video-player
            class="video-player-box"
            ref="videoPlayer"
            :options="playerOptions"
            :playsinline="true"
            customEventName="customstatechangedeventname"
            v-video-player:myVideoPlayer="playerOptions"
            @timeupdate="onPlayerTimeupdate($event)">
          </video-player>
        </div>
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
      showButton: false,
      playerOptions: {
        width: '360',
        sources: [{
          type: "video/mp4",
          src: "https://cdn.theguardian.tv/webM/2015/07/20/150716YesMen_synd_768k_vp8.webm"
        }],
        poster: start,
      }
    }
  },
  mounted(){
    console.log(window.innerWidth);
    if (window.innerWidth < 1000){
      this.playerOptions.width = parseInt(window.innerWidth)/1.2;
    }else{
      this.playerOptions.width = parseInt(window.innerWidth)/2.2;
    }
  },
  methods:{
    onPlayerTimeupdate(e){
      console.log(e)
      console.log(e.cache_.currentTime);
      if(e.cache_.currentTime>492){
        this.showButton = true;
      }
    },
    videoClick(e){
      console.log(e)
      console.log(this);
      console.log(this.player);
      if(this.player.paused()){
        this.player.play();
      }
      else{
        this.player.pause();
      }
    }
  },
  computed: {
      player() {
        return this.$refs.videoPlayer.player
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
  margin-top: 25% !important;
  margin-left: 40% !important;
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
  .vjs-big-play-button{
    margin-top: 20% !important;
    margin-left: 32% !important;
    width: 20vw;
  }
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
