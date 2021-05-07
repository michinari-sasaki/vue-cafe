<template>
  <li>
    <a :href="`/menu/` + id + `/`">
      <div class="item_list__tmb">
        <span v-if="image">
          <img :src="image.url" :alt="name" />
        </span>
        <span v-else>
          <img src="~@/assets/img/dammy.png" :alt="name" />
        </span>
      </div>
      <div class="item_list__detail">
        <div v-if="name">
          <p class="item_list__name">{{ name }}</p>
          <p class="item_list__price">¥{{ price }}</p>
        </div>
        <div v-else>
          <p class="item_list__name">商品情報未設定</p>
        </div>
      </div>
    </a>
  </li>
</template>

<script lang="ts">
import axios from 'axios'
import Vue from 'vue'
export default Vue.extend({
  name: 'LayoutItem',
  async asyncData({ $config }) {
    const menu = await axios.get(`${$config.apiUrl}/menu`, {
      headers: { 'X-API-KEY': $config.apiKey },
    })
    return {
      menuItems: menu.data.contents,
    }
  },
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
      default: '',
    },
    price: {
      type: String,
      required: true,
      default: '',
    },
    image: {
      required: true,
    },
  },
})
</script>
