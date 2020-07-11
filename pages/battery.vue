<template>
  <div>
    <my-header>{{ $options.name }}</my-header>
    <v-simple-table>
      <template v-slot:default>
        <tbody>
          <tr>
            <td>Battery Level</td>
            <td>{{ level * 100 }} %</td>
          </tr>

          <tr>
            <td>is charging</td>
            <td>{{ charging }}</td>
          </tr>

          <tr>
            <td>chargingTime</td>
            <td>{{ chargingTime }}</td>
          </tr>

          <tr>
            <td>dischargingTime</td>
            <td>{{ dischargingTime }}</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
  </div>
</template>

<script>
export default {
  name: 'Battery',
  data() {
    return {
      chargingTime: null,
      dischargingTime: null,
      level: null,
      charging: null,
    }
  },
  async mounted() {
    const battery = await window.navigator.getBattery()

    this.chargingTime = battery.chargingTime
    battery.onchargingtimechange = () => {
      this.chargingTime = battery.chargingTime
    }

    this.dischargingTime = battery.dischargingTime
    battery.ondischargingtimechange = () => {
      this.dischargingTime = battery.dischargingTime
    }

    this.charging = battery.charging
    battery.onchargingchange = () => {
      this.charging = battery.charging
    }

    this.level = battery.level
    battery.onlevelchange = () => {
      this.level = battery.level
    }
  },
}
</script>
