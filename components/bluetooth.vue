<template>
  <div>
    <v-btn large @click="connect">scan for devices</v-btn>
    <div v-if="device">
      <h2>connected to {{ deviceName }}</h2>
      <h2>{{ connected }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Bluetooth',
  data() {
    return {
      device: null,
      connected: false
    }
  },
  computed: {
    deviceName() {
      if (this.device) {
        if (this.device.name) {
          return this.device.name
        } else {
          return this.device.id
        }
      } else {
        return ''
      }
    }
  },
  methods: {
    async connect() {
      this.device = await navigator.bluetooth.requestDevice({
        acceptAllDevices: true
      })
      const server = await this.device.gatt.connect()
      this.connected = server.connected
    }
  }
}
</script>
