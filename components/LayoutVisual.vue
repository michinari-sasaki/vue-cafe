<template>
  <section class="fv">
    <h2 class="fv__heading">{{ title }}<slot></slot></h2>
  </section>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'LayoutVisual',
  props: {
    title: {
      type: String,
      default: '',
    },
  },
})
</script>
