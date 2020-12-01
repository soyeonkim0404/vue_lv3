<template>
  <div>
    <p v-for="item in this.$store.state.ask">
      <a v-bind:href="item.url">{{ item.title }}</a>
      <span>{{ item.user }} <small>{{ item.time_ago }}</small></span>
    </p>
  </div>
</template>

<script>
import { fetchAskList } from '../api/index.js';
export default {
  created(){
    this.$store.dispatch('FETCH_ASK');
  }
}
</script>

<style>

</style>