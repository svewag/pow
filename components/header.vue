<template>
  <v-banner color="purple" outlined class="mb-10">
    <v-btn small @click="back">< back</v-btn>
    <span class="slot ml-5"><slot /></span>
  </v-banner>
</template>

<script>
export default {
  name: 'Header',
  methods: {
    back() {
      this.$router.push('/')
    }
  }
}
</script>

<style lang="css">
.slot {
  font-size: 1.5rem;
}
</style>
