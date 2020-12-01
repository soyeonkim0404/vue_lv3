<template>
  <div>
    <p v-for="item in this.$store.state.news">
      <a v-bind:href="item.url">{{ item.title }}</a> | 
      <router-link v-bind:to="`/user/${item.user}`">{{ item.user }}</router-link> |
      <small>{{ item.time_ago }}</small>
    </p>
  </div>
</template>

<script>
import { fetchNewsList } from '../api/index.js';
export default {
  created() {
    //vuex 이용
    this.$store.dispatch('FETCH_NEWS');
  }
}
</script>

<style>

</style>