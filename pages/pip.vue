<template>
  <div>
    <my-header>{{ $options.name }}</my-header>
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
  name: 'PictureInPicture',
  data() {
    return {
      hasSupport: window.document.pictureInPictureEnabled,
      pipVideo: null,
    }
  },
  mounted() {
    const video = this.$refs.video

    video.addEventListener('enterpictureinpicture', function(event) {
      console.log('Entered PiP')
      const pipWindow = event.pictureInPictureWindow
      console.log(
        `Window size -  \n Width: ${pipWindow.width} \n Height: ${pipWindow.height}`
      )
    })

    video.addEventListener('leavepictureinpicture', function(event) {
      console.log('Left PiP')
    })
  },
  methods: {
    toggle() {
      if (!document.pictureInPictureElement) {
        this.$refs.video.requestPictureInPicture()
      } else {
        document.exitPictureInPicture()
      }
    },
  },
}
</script>

<style lang="css" scoped>
video {
  max-width: 800px;
  width: 100%;
}
</style>
