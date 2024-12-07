<template>
  <div class="progress-bar-container">
    <div class="progress-bar" :style="progressStyle"></div>
  </div>
</template>
  
<script>
  export default {
    props: {
      progress: {
        type: Number,
        required: true,
        default: 0
      }
    },

    computed: {
      progressStyle() {
        console.log('Recibiendo progress:', this.progress);  // Asegúrate de que se reciba el valor correcto
        return {
          width: `${this.progress}%`, // Usa el valor dinámico de progress
          height: '20px',
          backgroundColor: 'blue',
          borderRadius: '5px',
        };
      }
    }


  };
</script>
  
<style scoped>
.progress-bar-container {
  width: 100%;
  background-color: #f1f1f1;
  border-radius: 5px;
  overflow: hidden;
}


.progress-bar {
  height: 100%;
}

</style>
  