<template>
  <div class="content-main-container">
    <div class="header-section">
      <div class="title">
        <p>{{ title }}</p>
      </div>
    <div class="subtitle">
      <p>{{ subtitle }}</p>
    </div>
    </div>
    <div class="link-section">
      <div class="link-entry">
        <input placeholder="Enter a YouTube link" class="link-input">
      </div>
      <button class="search-video-button" @click="increaseProgress">Search Video</button>
    </div>
    <div class="progress-bar-section" v-show="isVisible">
      <label class="progressMessage">{{ progressMessage }}</label>
      <div class="progress-bar-group">
        <div  class="progress-bar">
        <ProgressBar :progress="progress" />
      </div>
      </div>
    </div>
  </div>
</template>
  
<script>
import ProgressBar from './ProgressBar.vue';
export default {
  name: 'ConverterSection',
  components:{
    ProgressBar,
  },

  data(){
    return{
      title: "Download and use your favorites YouTube videos",
      subtitle: "Enter your link YouTube Video",
      progressMessage: "We are finding your video",
      progress: 0,
      isVisible: false
    }
  },

  methods: {
    increaseProgress() {
      this.isVisible = true;
      console.log("start");
      if(this.progress == 100){
        this.progress = 0;
      }
      // Asegúrate de que el progreso se reinicie a 0 si ya está en 100%
      if (this.progress < 100) {
        console.log(this.progress)
        let increment = 100 / 10; // Incremento en 10 pasos (10 segundos)
        let counter = 0;
        let interval = setInterval(() => {
          counter++;
          this.progress = increment * counter; // Incrementa el progreso
          console.log(this.progress);
          if (counter >= 10) { // Detener el intervalo cuando llegue a 100%
            clearInterval(interval);
          }
        }, 1000); // Cada 1 segundo
      }

      console.log("end");
    },
  },

};
</script>
  
<style scoped>
input{
  font-family: "Outfit", sans-serif; 
  font-style: normal;
}

.content-main-container{
  width: 900px;
  height: 325px;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  /*border: 2px solid #000;*/
}

.header-section{
  width: 100%;
  height: 100px;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.title{
  font-size: 40px;
  font-weight: 600;
}

.subtitle{
  font-size: 25px;
  color: #5e5e5e;
}

.link-section{
  width: 100%;
  height: 125px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.link-input{
  width: 500px;
  height: 40px;
  margin-right: 10px;
  padding: 10px;
  border: none;
  border-radius: 5px;
  background-color: #f6f6f6;
}

.search-video-button{
  width: 100px;
  height: 40px;
  border: none;
  border-radius: 5px;
}

.progress-bar-section{
  width: 100%;
  height: 100px;
  padding-left: 25px;
  padding-right: 25px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  border: 0.5px solid #cacaca;
  border-radius: 5px;
}

.progressMessage{
  font-size: small;
  font-weight: 300;
}

.progress-bar-group{
  width: 100%;
  margin-top: 5px;
  display: flex;
}

.progress-bar{
  width: 100%;
  height: 100%;
}

</style>
  