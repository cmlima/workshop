<template>
  <div class="iframe-container" v-html="fixMapFrame(iframe)"></div>
</template>

<script>
export default {
  props: {
    iframe: {
      type: String,
      default: "",
    },
  },
  methods: {
    fixMapFrame(s) {
      return s
        .replace(/width=".+?"/, 'width="100%"')
        .replace(/height=".+?"/, 'height="100%"');
    },
  },
};
</script>

<style>
.iframe-container {
  width: 100vw;
  height: 400px;
  max-height: 400px;
}

.iframe-container iframe {
  pointer-events: none;
}
</style>