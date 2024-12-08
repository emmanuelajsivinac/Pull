<template>
  <div class="dashboard-main-container">
    <div class="header-section">
      <label></label>
    </div>
    <div class="content-section">
      <ConverterSectionBase />
    </div>
  </div>
</template>

<script>
import ConverterSectionBase from './ConverterSectionBase.vue'
export default {
    name: 'DashboardBase',
    components:{
      ConverterSectionBase,
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
  height: 15%;
  min-height: 100px;
  margin: 0;
  padding-left: 50px;
  display: flex;
  align-items: center;
}

.header-section, label{
  font-size: x-large;
  font-weight: 500;
}


.content-section{
  width: 100%;
  height: 85%;
  min-height: 400px;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
}
</style>
