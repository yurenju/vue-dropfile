<template>
  <div class="dropfile"
      :class="{ highlight: highlight }"
      @drop="drop"
      @dragover.prevent="dragover"
      @dragleave="dragleave">
  </div>
</template>

<script>
export default {
  name: 'dropfile',
  data() {
    return {
      highlight: false,
    };
  },
  methods: {
    drop(ev) {
      const transfer = ev.dataTransfer;
      if (transfer.files.length > 0) {
        this.$emit('drop', Array.from(transfer.files));
      } else {
        transfer.clearData();
      }
      this.highlight = false;
    },

    dragover() {
      this.highlight = true;
    },

    dragleave() {
      this.highlight = false;
    },
  },
};
</script>

<style scoped>
.dropfile {
  display: inline-block;
  min-height: 250px;
  min-width: 250px;
  border: 1px dashed #999;
}

.dropfile.highlight {
  border: 1px solid #999;
}
</style>
