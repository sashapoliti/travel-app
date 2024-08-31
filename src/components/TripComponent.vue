<template>
  <div
    id="trip-hero"
    :style="{ backgroundImage: 'url(' + store.trip.image_url + ')' }"
  >
    <div class="info">
      <h2>{{ store.trip.title }}</h2>
      <p>{{ store.trip.description }}</p>
      <p class="date">{{ store.trip.start_date }} | {{ store.trip.end_date }}</p>
    </div>
  </div>
</template>

<script>
import { store } from "../store/store.js";

export default {
  name: "TripComponent",
  data() {
    return {
      store,
    };
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
</style>
