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
    />
  </div>
</template>

<script>
export default {
  name: 'Camera',
  data () {
    return {
      front: false,
      stream: null
    }
  },
  watch: {
    stream () {
      this.$refs.video.srcObject = this.stream
    }
  },
  methods: {
    flip () {
      this.front = !this.front
      this.getVideo()
    },
    takePhoto () {
      const canvas = document.createElement('canvas')
      canvas.setAttribute('height', 1200)
      canvas.setAttribute('width', 1200)
      canvas
        .getContext('2d')
        .drawImage(this.$refs.video, 0, 0, 1200, 1200, 0, 0, 1200, 1200)
      const img = canvas.toDataURL('image/png')

      const saveImg = document.createElement('a')
      saveImg.href = img
      saveImg.download = 'imagename.png'
      saveImg.click()
    },
    async getVideo () {
      const constraints = {
        audio: true,
        video: {
          facingMode: this.front ? 'user' : 'environment'
        }
      }
      this.stream = await window.navigator.mediaDevices.getUserMedia({
        audio: true,
        video: true
      })
    }
  }
}
</script>

<style scoped>
video {
  width: 1000px;
  height: 560px;
}
</style>
