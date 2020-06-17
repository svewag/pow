<template>
  <section>
    <div class="color-scheme">
      <a
        href="https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme"
        >prefers-color-scheme</a
      >
    </div>
    <div class="reduced-motion">
      <a
        href="https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion"
        >prefers-reduced-motion</a
      >
    </div>
    <div class="contrast">
      <a
        href="https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-contrast"
        >prefers-contrast (not yet supported)</a
      >
    </div>
    <div class="reduced-transparency">
      <a
        href="https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-transparency"
        >prefers-reduced-transparency (not yet supported)</a
      >
    </div>
  </section>
</template>

<script>
export default {
  name: 'Css'
}
</script>

<style scoped>
div {
  padding: 10px;
}

a {
  text-decoration: underline;
}

@media (prefers-color-scheme: dark) {
  div.color-scheme {
    background: black;
  }
}

@media (prefers-color-scheme: light) {
  div.color-scheme {
    background: white;
  }
}

div.reduced-motion {
  animation: vibrate 0.3s linear infinite both;
}

@media (prefers-reduced-motion: reduce) {
  div.reduced-motion {
    animation: none;
  }
}

@keyframes vibrate {
  0% {
    transform: translate(0);
  }
  20% {
    transform: translate(-2px, 2px);
  }
  40% {
    transform: translate(-2px, -2px);
  }
  60% {
    transform: translate(2px, 2px);
  }
  80% {
    transform: translate(2px, -2px);
  }
  100% {
    transform: translate(0);
  }
}
</style>
