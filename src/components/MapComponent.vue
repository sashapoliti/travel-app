<template>
    <div id="map" ref="mapContainer"></div>
  </template>
  
  <script>
  export default {
    name: 'MapView',
    props: {
      latitude: {
        type: Number,
        required: true
      },
      longitude: {
        type: Number,
        required: true
      }
    },
    mounted() {
      this.initializeMap();
    },
    methods: {
      initializeMap() {
        const map = tt.map({
          key: 'bPvwZzqBzgA1AYzRQ4MXpFE3c0vsnBcD',
          container: this.$refs.mapContainer,
          center: [this.longitude, this.latitude],
          zoom: 14
        });
  
        const marker = new tt.Marker().setLngLat([this.longitude, this.latitude]).addTo(map);
      }
    }
  };
  </script>
  
  <style scoped>
  #map {
    height: 400px;
    width: 100%;
    border-radius: 10px;
  }
  </style>  