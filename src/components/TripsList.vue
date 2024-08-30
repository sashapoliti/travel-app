<template>
  <!-- add trip button -->
  <div class="add-card">
    <div class="add-card-content">
      <i class="fa-solid fa-plus"></i>
    </div>
  </div>

  <!-- trip buttons list -->
  <div
    v-for="trip in store.trips"
    class="trips add-card"
    :style="{ backgroundImage: 'url(' + trip.image_url + ')' }"
    @click="selectTrip(trip)"
  >
    <div class="add-card-content">
      <div class="info">
        <h2>{{ trip.place }}</h2>
      </div>
    </div>
  </div>
</template>

<script>
import { store } from "../store/store.js";

export default {
  name: "TripsList",
  data() {
    return {
      store,
    };
  },
  methods: {
    selectTrip(trip) {
      store.trip = trip;
      console.log(store.trip);      
    },
  },
};
</script>

<style lang="scss" scoped>
.add-card {
  width: 100%;
  border-radius: 20px;
  background-color: rgb(194, 194, 194);
  position: relative;
  padding-top: 45%; /* height / width proportion */
  margin-bottom: 2rem;
  cursor: pointer;
  .add-card-content {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    i {
      font-size: 2.5rem;
      font-weight: bold;
    }
  }
}

.trips {
  background-size: cover;
  background-position: center;
  .add-card-content {
    .info {
        position: absolute;
        top: 70%;
        left: 20px;
      h2 {
        color: white;
        font-size: 1.5rem;
        font-weight: 700;
      }
    }
  }
}
</style>
