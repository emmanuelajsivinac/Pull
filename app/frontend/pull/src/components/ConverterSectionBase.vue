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
    <div class="option-section">
      <!--<FinderVideoSection />-->
      <component :is="currentView" @changeView="changeComponent"/>
    </div>
  </div>
</template>
  
<script>
import FinderVideoSection from './FinderVideoSection.vue';
import DownloadVideoSection from './DownloadVideoSection.vue';

export default {
  name: 'ConverterSectionBase',
  components:{
    FinderVideoSection,
    DownloadVideoSection
  },

  data(){
    return{
      title: "Download and use your favorites YouTube videos",
      subtitle: "Enter your link YouTube Video",
      currentView : 'FinderVideoSection'
    }
  },

  methods:{

    changeComponent(newComponent) {
      this.currentView = newComponent;
    },

  }

};
</script>
  
<style scoped>
input{
  font-family: "Outfit", sans-serif; 
  font-style: normal;
}

.content-main-container{
  width: 900px;
  height: 400px;
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

.option-section{
  height: 300px;
  width: 100%;
}
</style>
  