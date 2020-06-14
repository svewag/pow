<template>
  <v-simple-table>
    <template v-slot:default>
      <tbody>
        <tr>
          <td>Cookie enabled?</td>
          <td>{{ navigator.cookieEnabled }}</td>
        </tr>

        <tr>
          <td>App-Version</td>
          <td>{{ navigator.appVersion }}</td>
        </tr>

        <tr>
          <td>Platform</td>
          <td>{{ navigator.platform }}</td>
        </tr>

        <tr>
          <td>Vendor</td>
          <td>{{ vendor }}</td>
        </tr>
      </tbody></template
    >

    <script>
      export default {
        name: 'Browser',
        data() {
          return {
            navigator: window ? window.navigator : null
          }
        },
        computed: {
          vendor() {
            if (this.navigator) {
              return [this.navigator.vendor, this.navigator.vendorSub]
                .filter(Boolean)
                .join(', ')
            }
            return ''
          }
        }
      }
    </script>
  </v-simple-table></template
>

<script>
export default {
  name: 'Browser',
  data() {
    return {
      navigator: window ? window.navigator : null
    }
  },
  computed: {
    vendor() {
      if (this.navigator) {
        return [this.navigator.vendor, this.navigator.vendorSub]
          .filter(Boolean)
          .join(', ')
      }
      return ''
    }
  }
}
</script>
