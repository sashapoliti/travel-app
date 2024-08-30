<template>
  <TripsList v-if="!(store.trip && Object.keys(store.trip).length > 0)" />
  <TripComponent v-if="store.trip && Object.keys(store.trip).length > 0" />
</template>

<script>
import { store } from '../store/store.js'
import TripsList from '../components/TripsList.vue'
import TripComponent from '../components/TripComponent.vue'

  export default {
    name: 'HomeView',
    components: {
        TripsList,
        TripComponent
    },
    data() {
      return {
        store
      }
    },    
  }
</script>

<style lang="scss" scoped>

</style>
