<template>
  <div>
    <my-header>{{ $options.name }}</my-header>
    <div class="onesignal-customlink-container"></div>
  </div>
</template>

<script>
export default {
  name: 'PushNotification',
  mounted() {
    this.$OneSignal.push(() => {
      this.$OneSignal.isPushNotificationsEnabled((isEnabled) => {
        if (isEnabled) {
          console.log('Push notifications are enabled!')
        } else {
          console.log('Push notifications are not enabled yet.')
        }
      })
    })
  },
}
</script>

<style lang="scss">
.onesignal-customlink-explanation {
  color: white !important;
}
</style>
