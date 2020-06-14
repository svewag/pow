<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
      <v-container
        v-for="item in items"
        :key="item"
      >
        <nuxt-link :to="item">
          <v-btn large>{{ item }}</v-btn>
        </nuxt-link>
      </v-container>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data () {
    return {
      items: ['battery', 'bluetooth', 'browser', 'camera']
    }
  }
}
</script>
