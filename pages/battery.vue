<template>
  <v-layout>
    <v-flex class="text-center">
      <battery />
    </v-flex>
  </v-layout>
</template>

<script>
import battery from '~/components/battery'

export default {
  components: {
    battery
  }
}
</script>
