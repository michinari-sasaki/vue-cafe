<template>
  <li>
    <a :href="`/news/` + id + `/`">
      <dl>
        <dt>{{ title }}</dt>
        <dd>{{ date }}</dd>
      </dl>
    </a>
  </li>
</template>

<script lang="ts">
import axios from 'axios'
import Vue from 'vue'
export default Vue.extend({
  name: 'LayoutNews',
  async asyncData({ $config }) {
    const info = await axios.get(`${$config.apiUrl}/news`, {
      headers: { 'X-API-KEY': $config.apiKey },
    })
    return {
      infoItems: info.data.contents,
    }
  },

  props: {
    title: {
      type: String,
      default: '',
    },
    date: {
      type: String,
      default: '',
    },
    id: {
      type: String,
      default: '',
    },
  },
})
</script>
