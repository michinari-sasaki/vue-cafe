<template>
  <div>
    <LayoutHeader />
    <LayoutVisual>
      VUE<br />CAFE<span>Happiness with coffee for you</span>
    </LayoutVisual>
    <div class="contents inner">
      <div class="news">
        <h3 class="heading__sub">News</h3>
        <ul class="news__list">
          <LayoutNews
            v-for="(item, index) in infoItems"
            :key="index"
            :id="item.id"
            :title="item.title"
            :date="$dateFns.format(new Date(item.date), 'yyyy.MM.dd.HH.mm')"
          />
        </ul>
        <p class="mt-3 mr-3 text-right lead">
          <a href="/news">more &gt;</a>
        </p>
      </div>

      <h3 class="heading__sub">Menu</h3>
      <ul class="item_list">
        <LayoutItem
          v-for="(item, index) in menuItems"
          :key="index"
          :id="item.id"
          :name="item.name"
          :image="item.image"
          :price="item.price"
        />
      </ul>
    </div>
    <LayoutFooter />
  </div>
</template>

<script lang="ts">
import axios from 'axios'
import Vue from 'vue'

export default Vue.extend({
  //name: "LayoutContent",
  async asyncData({ $config }) {
    const menu = await axios.get(`${$config.apiUrl}/menu`, {
      headers: { 'X-API-KEY': $config.apiKey },
    })
    const info = await axios.get(`${$config.apiUrl}/news?limit=1`, {
      headers: { 'X-API-KEY': $config.apiKey },
    })
    return {
      menuItems: menu.data.contents,
      infoItems: info.data.contents,
    }
  },
  props: {},
  data: function () {
    return {}
  },
  methods: {
    addTodo: function () {},
  },
  mounted: function () {},
})
</script>

<style lang="scss"></style>
