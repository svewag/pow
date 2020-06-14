<template>
  <div>
    <v-btn @click="getVideo">open camera</v-btn>
    <v-btn @click="flip">flip camera</v-btn>
    <v-btn @click="takePhoto">take a photo</v-btn>

    <video
      v-show="stream"
      ref="video"
      autoplay
      muted
      controls
      playsinline="true"
    />

    <a v-show="image" ref="download" download="photo.png">download</a>
  </div>
</template>

<script>
export default {
  name: 'Camera',
  data() {
    return {
      front: false,
      stream: null,
      image: null
    }
  },
  watch: {
    stream() {
      this.$refs.video.srcObject = this.stream
    },
    image() {
      this.$refs.download.href = this.image
    }
  },
  methods: {
    flip() {
      this.front = !this.front
      this.getVideo()
    },
    takePhoto() {
      const canvas = document.createElement('canvas')
      canvas.setAttribute('height', 1200)
      canvas.setAttribute('width', 1200)
      canvas
        .getContext('2d')
        .drawImage(this.$refs.video, 0, 0, 1200, 1200, 0, 0, 1200, 1200)

      this.image = canvas.toDataURL('image/png')
    },
    async getVideo() {
      const constraints = {
        audio: true,
        video: {
          facingMode: this.front ? 'user' : 'environment'
        }
      }
      this.stream = await window.navigator.mediaDevices.getUserMedia(
        constraints
      )
    }
  }
}
</script>

<style scoped>
video {
  width: 100%;
}
</style>
