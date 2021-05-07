<template>
  <div>
    <LayoutHeader />
    <LayoutVisual title="About" />
    <div class="contents inner">
      <h3 class="heading__sub">About</h3>
      <p class="mt-5 h4 lh-2 text-center">
        このサイトはサンプルサイトです。<br />Vue.js, TypeScript, BootStrap<br />
        Axios, Nuxt.js ,Netlify, microCMS<br />等を使用して作成しています。<br />
      </p>
    </div>
    <LayoutFooter />
  </div>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  data: function () {
    return {}
  },
})
</script>

<style lang="scss" scoped>
.fv {
  height: 20vh;
}
.heading__sub {
  text-align: center;
}
</style>
