<template>
  <!-- Hero -->
  <div
    id="trip-hero"
    :style="{ backgroundImage: 'url(' + store.trip.image_url + ')' }"
  >
    <div class="info">
      <h2>{{ store.trip.title }}</h2>
      <p>{{ store.trip.description }}</p>
      <p class="date">
        {{ store.trip.start_date }} | {{ store.trip.end_date }}
      </p>
    </div>
  </div>

  <!-- Days -->
  <div v-for="day in store.trip.days" :key="day.id" class="days-card">
    <div class="info">
      <h2>{{ day.title }}</h2>
      <p>{{ day.description }}</p>
      <p class="date">{{ day.date }}</p>

      <!-- Stages -->
      <div
        v-for="stage in day.stages"
        :key="stage.id"
        class="stages-card"
        @click="openMapModal(stage.latitude, stage.longitude)"
      >
        <div class="info-stage">
          <h4><i class="fa-solid fa-circle-dot"></i> {{ stage.title }}</h4>
          <p>{{ stage.description }}</p>
          <p class="date">{{ stage.start_time }} - {{ stage.end_time }}</p>
        </div>
      </div>
    </div>
  </div>

  <!-- Map Modal -->
  <MapModal
    :latitude="modalLatitude"
    :longitude="modalLongitude"
    :visible="isMapModalVisible"
    @close="closeMapModal"
  />
</template>

<script>
import { store } from "../store/store.js";
import MapModal from "../components/MapModal.vue";

export default {
  name: "TripComponent",
  components: {
    MapModal,
  },
  data() {
    return {
      store,
      isMapModalVisible: false,
      modalLatitude: null,
      modalLongitude: null,
    };
  },
  methods: {
    openMapModal(latitude, longitude) {
      this.modalLatitude = latitude;
      this.modalLongitude = longitude;
      this.isMapModalVisible = true;
    },
    closeMapModal() {
      this.isMapModalVisible = false;
      this.modalLatitude = null;
      this.modalLongitude = null;
    },
  },
};
</script>

<style lang="scss" scoped>
#trip-hero {
  position: relative;
  width: 100%;
  padding-top: 110%;
  background-size: cover;
  border-radius: 0 10% 0 10%;
  .info {
    color: white;
    position: absolute;
    bottom: 5%;
    left: 0;
    padding: 0 2rem;
    h2 {
      font-size: 1.5rem;
      font-weight: 900;
    }
    p {
      font-size: 0.7rem;
      font-weight: 700;
      &.date {
        font-size: 0.5rem;
        font-style: italic;
      }
    }
  }
}

.days-card {
  margin-top: 1rem;
  .info {
    .stages-card {
      border-radius: 10px;
      padding: 0.3rem;
      margin-top: 0.6rem;
      cursor: pointer;
      &:hover {
        background-color: #f2f2f2;
      }
    }
  }
}
</style>
