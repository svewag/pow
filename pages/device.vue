<template>
  <div>
    <my-header>{{ $options.name }}</my-header>
    <v-simple-table>
      <template v-slot:default>
        <tbody>
          <tr>
            <td>RAM</td>
            <td>{{ navigator.deviceMemory }} GB</td>
          </tr>

          <tr>
            <td>CPU</td>
            <td>{{ navigator.hardwareConcurrency }} Cores</td>
          </tr>
        </tbody></template
      >
    </v-simple-table>
  </div>
</template>

<script>
export default {
  name: 'Device',
  data() {
    return {
      navigator: window.navigator,
    }
  },
}
</script>
