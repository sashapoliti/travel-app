<template>
  <header>
    <h1>WanderNote</h1>
  </header>

  <RouterView />
</template>

<script>
import { RouterLink, RouterView } from 'vue-router';
import { store } from './store/store.js';

export default {
  name: 'App',
  data() {
    return {
      store
    };
  },
  methods: {
    
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
