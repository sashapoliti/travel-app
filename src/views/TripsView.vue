<template>
    <div>
      <h1>Lista dei Viaggi</h1>
      <div v-for="trip in trips" :key="trip.id" class="trip">
        <h2>{{ trip.title }} - {{ trip.place }}</h2>
        <p>{{ trip.description }}</p>
        <p><strong>Data Inizio:</strong> {{ trip.start_date }} | <strong>Data Fine:</strong> {{ trip.end_date }}</p>
  
        <div v-for="day in trip.days" :key="day.id" class="day">
          <h3>{{ day.title }} - {{ day.date }}</h3>
          <p>{{ day.description }}</p>
  
          <div v-for="stage in day.stages" :key="stage.id" class="stage">
            <h4>{{ stage.title }}</h4>
            <p>{{ stage.description }}</p>
            <p><strong>Orario:</strong> {{ stage.start_time }} - {{ stage.end_time }}</p>
            <p><strong>Valutazione:</strong> {{ stage.rating }} stelle</p>
            <p><strong>Note:</strong> {{ stage.note }}</p>
            <img :src="stage.image_url" alt="Stage image" class="stage-image" />
            <p><strong>Posizione:</strong> Lat: {{ stage.latitude }}, Lng: {{ stage.longitude }}</p>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        trips: [],
      };
    },
    created() {
      // Fetch dei dati dal file JSON
      fetch('/trips.json')
        .then(response => response.json())
        .then(data => {
          this.trips = data;
        })
        .catch(error => {
          console.error('Errore nel caricamento dei dati:', error);
        });
    },
  };
  </script>
  
  <style scoped>
  .trip {
    border: 1px solid #ddd;
    padding: 20px;
    margin-bottom: 20px;
  }
  .day {
    margin-left: 20px;
    padding: 10px;
    border-left: 3px solid #ddd;
  }
  .stage {
    margin-left: 20px;
    padding: 10px;
    border-left: 3px solid #aaa;
  }
  .stage-image {
    width: 100px;
    height: auto;
    margin-top: 10px;
  }
  </style>
  