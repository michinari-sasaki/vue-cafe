<template>
  <footer>@ {{ copyDate }} VueCafe</footer>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  data: function () {
    return {
      copyDate: 0,
    }
  },
  methods: {
    getYear: function () {
      this.copyDate = new Date().getFullYear()
    },
  },
  mounted: function () {
    this.getYear()
  },
})
</script>

<style></style>
