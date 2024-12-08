<template>
  <div class="download-section">
    <div class="info-options-section">
      <div class="info-video">
          <div class="item">
              <div class="icon">
              </div>
              <div class="name"></div>
              <div>
                  {{ videoName }}
              </div>
          </div>
      </div>
      <div class="arrow-icon">
      </div>
      <div class="converter-options">
          <div class="item-options">
              <div class="options-label">{{ optionsLabel }}</div>
              <div class="line-v"></div>
              <div class="options-list">mp3</div>
          </div>
      </div>
    </div>
    <div class="convert-button-section">
      <button @click="increaseProgress">Download</button>
    </div>
    <ModalBase 
      v-if="showModal"
      :isOpen="showModal"
      title= ""
      message=""
      @close="closeModal"
      @confirm="confirmChange">
      <div class="download-notification-section">
        File succesfully downloaded!
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
        videoName: "Oficial Video | this is a example result",
        optionsLabel:"File format to Download",
        progressMessage: "We are downloading your video",
        progress: 0,
        isVisible: false,
        showModal: false,
        videoFoundTitle: "Oficial Video | this is a example result",
        internalHeaderMessage: "This is your video, rigth?",
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
        this.$emit('changeView', 'FinderVideoSection');
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
  .download-section{
    box-sizing: content-box;
    height: 100%;
    width: 100%;
  }
  

  .info-options-section{
    height: 150px;
    width: 100%;
    display: flex;
  }

  .info-video{
    box-sizing: border-box;
    height: 100%;
    width: 100%;
    padding-left: 10px;
    padding-right: 10px;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .item{
    width: 100%;
    height: 60px;
    padding: 10px;
    display: flex;
    align-items: center;
    border: none;
    border-radius: 5px;
    background-color: #f5f5f5;
  }

  .arrow-icon{
    width: 100px;
    height: 100%;
  }

  .converter-options{
    height: 100%;
    width: 100%;
    padding-left: 10px;
    padding-right: 10px;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .item-options{
    width: 100%;
    height: 60px;
    padding: 10px;
    display: flex;
    border: none;
    border-radius: 5px;
    background-color: #f5f5f5;
  }

  .options-label{
    width: 75%;
    height: 100%;
    display: flex;
    align-items: center;
  }

  .line-v{
    height: 100%;
    width: 1px;
    background-color: #000;
  }

  .options-list{
    width: 25%;
    height: 100%;
    padding-left: 10px;
    padding-right: 10px;
    display: flex;
    align-items: center;
  }

  .convert-button-section{
    height: 50px;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .convert-button-section button{
    height: 50px;
    width: 150px;
    margin-bottom: 20px;
    border: none;
    border-radius: 5px;
    font-family: "Outfit", sans-serif; 
    font-style: normal;
    font-size: medium;
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

  .download-notification-section{
    margin-bottom: 20px;
  }
</style>