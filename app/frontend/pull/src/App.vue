<script setup>
import DashboardBase from './components/DashboardBase.vue'
</script>

<template>
  <div class="main-container">
    <DashboardBase/>
  </div>
</template>

<style scoped>
  .main-container {
    height: 100%;
    width: 100%;
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
</style>
