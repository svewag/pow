<template>
  <div>
    <my-header>{{ $options.name }}</my-header>
    <unsupported v-show="!hasSupport" />
    <p>
      You must install this pwa and open it. After providing a badge number in
      the input below, you can see a badge added to the app icon in the dock or
      task switcher.
    </p>
    <v-text-field
      v-model="badgeValue"
      type="number"
      label="badge value (only numbers)"
    />
  </div>
</template>

<script>
export default {
  name: 'Badge',
  data() {
    return {
      badgeValue: null,
      hasSupport: 'setAppBadge' in navigator,
    }
  },
  watch: {
    badgeValue() {
      if (this.badgeValue !== null) {
        if (this.badgeValue === '') {
          navigator.clearAppBadge()
        } else {
          navigator.setAppBadge(this.badgeValue)
        }
      }
    },
  },
}
</script>
