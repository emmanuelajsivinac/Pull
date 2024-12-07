<template>
  <div class="dashboard-main-container">
    <div class="header-section">
      <label>pull</label>
    </div>
    <div class="content-section">
      <ConverterSection />
    </div>
  </div>
</template>

<script>
import ConverterSection from './ConverterSection.vue'
export default {
    name: 'DashboardBase',
    components:{
      ConverterSection,
    }
};
</script>

<style scoped>
.dashboard-main-container{
  width: 100%;
  height: 100vh;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.header-section{
  box-sizing: border-box;
  width: 100%;
  height: 20%;
  min-height: 100px;
  margin: 0;
  padding-top: 30px;
  padding-left: 50px;
  display: flex;
  align-items: center;
}

.header-section, label{
  font-size: xx-large;
  font-weight: 500;
}


.content-section{
  width: 100%;
  height: 80%;
  min-height: 400px;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
}
</style>
