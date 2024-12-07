<template>
  <div class="dashboard-main-container">
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
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
