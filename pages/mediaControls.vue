<template>
  <div>
    <my-header>{{ $options.name }}</my-header>
    <unsupported v-show="!hasSupport" />
    <video ref="video" width="400" controls>
      <source
        src="https://mdn.github.io/learning-area/javascript/apis/video-audio/finished/video/sintel-short.mp4"
        type="video/mp4"
      />
    </video>
    <p>
      Start the video and then use your media keys to pause and play again.
    </p>
    <p>
      When you are on desktop, have a look at the right side of your browser.
      <br />There is a media control panel with custom artwork and information
      on the media.
    </p>
    <p>
      When you are on mobile, have a look at your lock screen to finde the media
      controls.
    </p>
  </div>
</template>

<script>
export default {
  name: 'MediaControls',
  data() {
    return {
      hasSupport: 'mediaSession' in navigator,
    }
  },
  mounted() {
    if ('mediaSession' in navigator) {
      navigator.mediaSession.metadata = new window.MediaMetadata({
        title: 'The title',
        artist: 'The Artist',
        album: 'The Album',
        artwork: [
          {
            src: 'https://via.placeholder.com/96/96',
            sizes: '96x96',
            type: 'image/png',
          },
          {
            src: 'https://via.placeholder.com/128/128',
            sizes: '128x128',
            type: 'image/png',
          },
          {
            src: 'https://via.placeholder.com/192/192',
            sizes: '192x192',
            type: 'image/png',
          },
          {
            src: 'https://via.placeholder.com/256/256',
            sizes: '256x256',
            type: 'image/png',
          },
          {
            src: 'https://via.placeholder.com/384/384',
            sizes: '384x384',
            type: 'image/png',
          },
          {
            src: 'https://via.placeholder.com/512/512',
            sizes: '512x512',
            type: 'image/png',
          },
        ],
      })

      navigator.mediaSession.setActionHandler('play', () => {
        this.$refs.video.play()
      })
      navigator.mediaSession.setActionHandler('pause', () => {
        this.$refs.video.pause()
      })
    }
  },
}
</script>
