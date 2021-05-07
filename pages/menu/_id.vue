<template>
  <div>
    <LayoutHeader />
    <div class="contents inner">
      <ul class="item_list__column">
        <li v-if="item.image" class="item_list__tmb">
          <img :src="item.image.url" :alt="item.name" />
        </li>
        <li v-else class="item_list__tmb">
          <img src="~@/assets/img/dammy.png" :alt="item.name" />
        </li>
        <li class="item_list__detail">
          <div v-if="item.name">
            <p class="item_list__name">{{ item.name }}</p>
            <p class="h5 mt-2">{{ item.type }}</p>
            <p class="item_list__price mt-4">¥{{ item.price }}</p>
            <p class="h4 mt-5 lh-2">{{ item.description }}</p>
          </div>
          <div v-else>
            <p class="item_list__name">商品情報未設定</p>
          </div>
        </li>
      </ul>
    </div>
    <LayoutFooter />
  </div>
</template>

<script lang="ts">
import axios from 'axios'
import Vue from 'vue'
export default Vue.extend({
  async asyncData({ $config, params, error }) {
    const { data } = await axios.get(`${$config.apiUrl}/menu/${params.id}`, {
      headers: { 'X-API-KEY': $config.apiKey },
    })
    return {
      item: data,
    }
  },
})
</script>

<style lang="scss"></style>
