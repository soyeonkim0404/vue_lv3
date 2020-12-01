<template>
  <div>
    <p v-for="item in this.$store.state.jobs">
      <span>[{{ item.type }}]</span>
      <a v-bind:href="item.url">{{ item.title }}</a>
      <span><small>{{ item.time_ago }}</small></span>
    </p>
  </div>
</template>

<script>
import { fetchJobsList } from '../api/index.js';
export default {
  created(){
    this.$store.dispatch('FETCH_JOBS');
  }
}
</script>

<style>

</style>