<template>
  <v-flex>
    <div v-for="item in items" :key="item" class="mx-2 my-2 float-left">
      <v-btn :to="item" nuxt large>{{ item }}</v-btn>
    </div>
  </v-flex>
</template>

<script>
export default {
  data() {
    return {
      items: [
        'battery',
        'bluetooth',
        'browser',
        'camera',
        'credentials',
        'css',
        'device',
        'geolocation',
        'network',
        'pip',
        'mediaControls',
        'badge',
      ],
    }
  },
}
</script>
