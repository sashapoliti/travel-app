<template>
  <header>
    <h1>WanderNote</h1>
  </header>

  <RouterView />
</template>

<script>
import { RouterLink, RouterView } from "vue-router";
import { store } from "./store/store.js";
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      store,
    };
  },
  methods: {
    getTrips() {
      axios
        .get("/trips.json")
        .then((response) => {
          this.store.trips = response.data;
          console.log(this.store.trips);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
  mounted() {
    this.getTrips();
    console.log(this.store.trip);
  },
};
</script>

<style scoped lang="scss">
header {
  margin-bottom: 1.5rem;
  line-height: 1.5;
  display: flex;
  h1 {
    font-size: 2rem;
    font-weight: 700;
  }
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}
</style>
