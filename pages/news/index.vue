<template>
  <div>
    <LayoutHeader />
    <div class="contents inner">
      <div class="news">
        <h3 class="heading__sub text-center">News</h3>
        <ul class="news__list">
          <LayoutNews
            v-for="(item, index) in infoItems"
            :key="index"
            :id="item.id"
            :title="item.title"
            :date="$dateFns.format(new Date(item.date), 'yyyy.MM.dd.HH.mm')"
          />
        </ul>
        <p class="mt-3 ml-3 text-left lead">
          <a href="/">&lt; back</a>
        </p>
      </div>
    </div>

    <LayoutFooter />
  </div>
</template>

<script lang="ts">
import axios from 'axios'
import Vue from 'vue'

export default Vue.extend({
  async asyncData({ $config }) {
    const info = await axios.get(`${$config.apiUrl}/news`, {
      headers: { 'X-API-KEY': $config.apiKey },
    })
    return {
      infoItems: info.data.contents,
    }
  },
  data: function () {},
  methods: {
    addTodo: function () {},
  },
  mounted: function () {},
})
</script>

<style lang="scss"></style>
