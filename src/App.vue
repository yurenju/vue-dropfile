<template>
  <div id="app">
    <dropfile @drop="getFiles"></dropfile>
  </div>
</template>

<script>
import Hello from './components/Hello';
import Dropfile from './components/Dropfile';

export default {
  name: 'app',
  components: {
    Hello, Dropfile,
  },
  methods: {
    getFiles(files) {
      console.log(files);
    },
  },
  mounted() {
    /* global window */
    window.addEventListener('dragover', e => e.preventDefault(), false);
    window.addEventListener('drop', e => e.preventDefault(), false);
  },
};
</script>
