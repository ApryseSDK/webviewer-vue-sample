<template>
  <div id="app">
    <WebViewer
      initialDoc="https://pdftron.s3.amazonaws.com/downloads/pl/demo-annotated.pdf"
    />
  </div>
</template>

<script>
import WebViewer from "./components/WebViewer.vue";

export default {
  name: "App",
  components: {
    WebViewer,
  },
};
</script>

<style>
html,
body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0 auto;
}
</style>
