<template>
  <div class="finder-section">
    <div class="link-section">
      <div class="link-entry">
        <input placeholder="Enter a YouTube link" class="link-input">
      </div>
      <button class="search-video-button" @click="increaseProgress">Search Video</button>
    </div>
    <ModalBase 
      v-if="showModal"
      :isOpen="showModal"
      title= ""
      message="¿Estás seguro de realizar esta acción?"
      @close="closeModal"
      @confirm="confirmChange">
      <div class="video-found-section">
        <h2>{{ internalHeaderMessage }}</h2>
        <div class="video-found-image-preview">
        </div>
        <div class="video-found-title">
          <label>{{ videoFoundTitle }}</label>
        </div>
      </div>
    </ModalBase>
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
import ModalBase from './modalBase.vue';

export default {
  name: 'FinderVideoSection',
  components:{
    ProgressBar,
    ModalBase
  },

  data(){
    return{
      progressMessage: "We are searching your video",
      progress: 0,
      isVisible: false,
      showModal: false,
      videoFoundTitle: "Oficial Video | this is a example result",
      internalHeaderMessage: "This is your video, rigth?"
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

      if(this.progress == 100){
        this.openModal();
      }

      console.log("end");
    },

    openModal() {
      this.showModal = true;
    },

    closeModal() {
      this.showModal = false;
    },

    confirmChange() {
      this.$emit('changeView', 'DownloadVideoSection');
      this.closeModal();
    },

  },

  watch: {
    progress(newVal) {
      if (newVal === 100) {
        this.openModal();
        this.isVisible = false;
      }
    },
  },
};
</script>

<style scoped>
.finder-section{
  height: 100%;
  width: 100%;
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
  font-family: "Outfit", sans-serif; 
  font-style: normal;
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

.video-found-section{
  width: 100%;
  margin-bottom: 20px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.video-found-section h2{
  margin: 0;
  padding: 0;
}

.video-found-image-preview{
  width: 300px;
  height: 150px;
  margin-top: 10px;
  margin-bottom: 10px;
  background-color: #8f8f8f;
}
</style>