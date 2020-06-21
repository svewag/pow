<template>
  <div>
    <unsupported v-show="!hasSupport" />
    <video
      ref="video"
      loop
      controls
      autoplay
      width="400"
      playsinline="true"
      src="~/assets/video.mp4"
    ></video>
    <br />
    <v-btn large @click="toggle">toggle pip</v-btn>
  </div>
</template>

<script>
export default {
  name: 'Pip',
  data() {
    return {
      hasSupport: window.document.pictureInPictureEnabled
    }
  },
  methods: {
    toggle() {
      if (!document.pictureInPictureElement) {
        this.$refs.video.requestPictureInPicture()
      } else {
        document.exitPictureInPicture()
      }
    }
  }
}
</script>
