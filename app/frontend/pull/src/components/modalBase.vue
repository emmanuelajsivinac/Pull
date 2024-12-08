<template>
    <div class="modal-overlay" v-if="isOpen">
      <div class="modal-container">
        <div class="modal-header">
          <p>{{ title }}</p>
          <button class="close-button" @click="closeModal">X</button>
        </div>
        <div class="modal-body">
          <slot>
          {{ message }}
          </slot>
        </div>
        <div class="modal-footer">
          <button @click="closeModal">Cancel</button>
          <button @click="confirmAction">Accept</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "ModalBase",
    props: {
      title: {
        type: String,
        default: "Título del Modal",
      },
      message: {
        type: String,
        default: "Mensaje del modal",
      },
      isOpen: {
        type: Boolean,
        required: true,
      },
    },
    emits: ["close", "confirm"],
    methods: {
      closeModal() {
        this.$emit("close"); // Emitimos el evento para cerrar el modal
      },
      confirmAction() {
        this.$emit("confirm"); // Emitimos el evento para confirmar acción
      },
    },
  };
  </script>
  
  <style scoped>
  .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }
  
  .modal-container {
    box-sizing: content-box;
    padding: 20px;
    width: 500px;
    border-radius: 10px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
    background: #fff;
  }
  
  .modal-header {
    box-sizing: border-box;
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-weight: 300;
  }
  
  .modal-body{
    box-sizing: border-box;
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
  }

  .modal-footer {
    box-sizing: content-box;
    width: 100%;
    padding: 0;
    margin: 0;
    display: flex;
    gap: 10px;
  }

  .modal-footer button{
    height: 30px;
    width: 100%;
    padding: 5px;
    border: none;
    border-radius: 5px;
    font-family: "Outfit", sans-serif; 
    font-style: normal;
  }
  
  .close-button {
    border: none;
    background: transparent;
    font-size: 16px;
    cursor: pointer;
  }
  </style>
  