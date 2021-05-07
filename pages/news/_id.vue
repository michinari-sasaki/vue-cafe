<template>
  <div>
    <LayoutHeader />
    <div class="contents inner">
      <div class="news">
        <h3 class="heading__sub text-center">News</h3>
        <ul class="news__list">
          <li>
            <a>
              <dl>
                <dt class="h2 font-weight-bold">{{ item.title }}</dt>
                <dd>
                  {{ $dateFns.format(new Date(item.date), 'yyyy.MM.dd.HH.mm') }}
                </dd>
              </dl>
              <div class="h4 lh-2 mt-5">
                {{ item.description }}
              </div>
            </a>
          </li>
        </ul>
        <p class="mt-3 ml-3 text-left lead">
          <a href="/news">&lt; News一覧へ</a>
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
  async asyncData({ $config, params, error }) {
    const { data } = await axios.get(`${$config.apiUrl}/news/${params.id}`, {
      headers: { 'X-API-KEY': $config.apiKey },
    })
    return {
      item: data,
    }
  },
})
</script>

<style lang="scss"></style>
