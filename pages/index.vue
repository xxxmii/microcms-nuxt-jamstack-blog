<template>
  <ul>
    <li v-for="content in contents" :key="content.id">
      <nuxt-link :to="`/${content.id}`">{{ content.title }}</nuxt-link>
    </li>
  </ul>
</template>

<script>
import axios from "axios";
export default {
  async asyncData({ $config }) {
    const { data } = await axios.get(
      "https://xxxmii-blog.microcms.io/api/v1/blog",
      {
        headers: {
          "X-API-KEY": $config.apiKey,
        },
      }
    );
    return data;
  },
};
</script>