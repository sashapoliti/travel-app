<template>
  <div id="trip-hero" :style="{ backgroundImage: 'url(' + store.trip.image_url + ')' }">

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
}
</style>
