<template>
  <div class="header">
      <router-link to="/news">News</router-link> |
      <router-link to="/ask">Ask</router-link> |
      <router-link to="/jobs">Jobs</router-link>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.header{
    display:flex;
    background:pink;
    padding:8px;
    color:#fff;
    font-size: 2rem;
}

.header a{
    padding:0 15px;
    color:#fff;
    text-decoration: none;
}

.header .router-link-exact-active{
    color:purple;
}
</style>