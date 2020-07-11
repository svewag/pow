<template>
  <div>
    <my-header>{{ $options.name }}</my-header>
    <unsupported v-show="!hasSupport" />
    <v-btn large @click="connect">scan</v-btn>
    <v-simple-table v-if="device">
      <template v-slot:default>
        <tbody>
          <tr>
            <td>device name</td>
            <td>{{ deviceName }}</td>
          </tr>
          <tr>
            <td>connected</td>
            <td>{{ connected }}</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
  </div>
</template>

<script>
export default {
  name: 'Bluetooth',
  data() {
    return {
      hasSupport: 'bluetooth' in navigator,
      device: null,
      connected: false,
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
    },
  },
  methods: {
    async connect() {
      this.device = await navigator.bluetooth.requestDevice({
        acceptAllDevices: true,
      })
      const server = await this.device.gatt.connect()
      this.connected = server.connected
    },
  },
}
</script>
