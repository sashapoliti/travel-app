<template>
    <div v-if="visible" class="modal-overlay" @click="closeModal">
      <div class="modal-content" @click.stop>
        <MapComponent :latitude="latitude" :longitude="longitude" />
      </div>
    </div>
  </template>
  
  <script>
  import MapComponent from './MapComponent.vue';
  
  export default {
    name: 'MapModal',
    components: {
      MapComponent
    },
    props: {
      latitude: {
        type: Number,
        required: true
      },
      longitude: {
        type: Number,
        required: true
      },
      visible: {
        type: Boolean,
        required: true
      }
    },
    methods: {
      closeModal() {
        this.$emit('close');
      }
    }
  };
  </script>
  
  <style scoped>
  .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.7);
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .modal-content {
    background: white;
    border-radius: 10px;
    width: 80%;
    max-width: 600px;
    height: 400px;
  }
  </style>
  