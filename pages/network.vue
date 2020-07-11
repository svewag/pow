<template>
  <div>
    <my-header>{{ $options.name }}</my-header>
    <v-simple-table>
      <template v-slot:default>
        <tbody>
          <tr>
            <td>
              Online<help
                href="https://developer.mozilla.org/en-US/docs/Web/API/NavigatorOnLine/onLine"
              />
            </td>
            <td>{{ online }}</td>
          </tr>
          <tr>
            <td>
              Data-Saver<help
                href="https://developer.mozilla.org/en-US/docs/Web/API/NetworkInformation/saveData"
              />
            </td>
            <td>{{ navigator.connection.saveData }}</td>
          </tr>
          <tr>
            <td>
              Effective-Type<help
                href="https://developer.mozilla.org/en-US/docs/Web/API/NetworkInformation/effectiveType"
              />
            </td>
            <td>
              {{ navigator.connection.effectiveType }}
            </td>
          </tr>
          <tr>
            <td>
              Type<help
                href="https://developer.mozilla.org/en-US/docs/Web/API/NetworkInformation/type"
              />
            </td>
            <td>
              {{ navigator.connection.type }}
            </td>
          </tr>
          <tr>
            <td>
              Downlink
              <help
                href="https://developer.mozilla.org/en-US/docs/Web/API/NetworkInformation/downlink"
              />
            </td>
            <td>{{ navigator.connection.downlink }}</td>
          </tr>
          <tr>
            <td>
              RTT<help
                href="https://developer.mozilla.org/en-US/docs/Web/API/NetworkInformation/rtt"
              />
            </td>
            <td>{{ navigator.connection.rtt }}</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
  </div>
</template>

<script>
export default {
  name: 'Network',
  data() {
    return {
      navigator: window.navigator,
      online: navigator.onLine,
    }
  },
  mounted() {
    const getOnlineStatus = () => {
      this.online = navigator.onLine
    }

    window.addEventListener('online', getOnlineStatus)
    window.addEventListener('offline', getOnlineStatus)
  },
}
</script>
