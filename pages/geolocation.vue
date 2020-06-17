<template>
  <div>
    <v-btn large @click="start">start watch</v-btn>
    <v-btn large @click="end">end watch</v-btn>
    <div>{{ coords }}</div>
  </div>
</template>

<script>
export default {
  name: 'Geolocation',
  data() {
    return {
      latitude: null,
      longitude: null,
      watchID: null
    }
  },
  computed: {
    coords() {
      if (this.latitude && this.longitude) {
        return [this.latitude, this.longitude].join(' / ')
      }

      return ''
    }
  },
  methods: {
    syncCoords(position) {
      this.latitude = position.coords.latitude
      this.longitude = position.coords.longitude
    },
    start() {
      if ('geolocation' in window.navigator) {
        navigator.geolocation.getCurrentPosition(this.syncCoords)
        this.watchID = window.navigator.geolocation.watchPosition(
          this.syncCoords
        )
      }
    },
    end() {
      navigator.geolocation.clearWatch(this.watchID)
    }
  }
}
</script>
