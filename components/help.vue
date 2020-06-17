<template>
  <v-btn icon :href="href"
    ><v-icon small>mdi-help-circle-outline</v-icon></v-btn
  >
</template>

<script>
export default {
  name: 'Help',
  props: {
    href: {
      type: String,
      required: true
    }
  }
}
</script>
