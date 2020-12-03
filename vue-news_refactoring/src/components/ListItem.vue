<template>
  <div>
    <ul class="news-list">
      <li v-for="item in listItems" class="post">
        <div class="points">{{ item.points || 0 }}</div>
        <div class="news-title">
            <template v-if="item.domain">
                <a v-bind:href="item.url">{{ item.title }}</a>
            </template>
            <template v-else>
                <router-link v-bind:to="`item/${item.id}`">
                    {{ item.title }}
                </router-link>
            </template>
        </div>
        <div class="news-options">
          by
          <router-link v-if="item.user" v-bind:to="`/user/${item.user}`">{{ item.user }}</router-link>
          <a v-bind:href="item.url" v-else>{{ item.domain }}</a>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import { fetchNewsList } from '../api/index.js';
export default {
  created() {
    const name = this.$route.name;
    if(name === 'news'){
        this.$store.dispatch('FETCH_NEWS');
    }else if(name === 'ask'){
        this.$store.dispatch('FETCH_ASK');
    }else if(name === 'jobs'){
        this.$store.dispatch('FETCH_JOBS');
    }
  },
  computed: {
      listItems() {
        const name = this.$route.name;
        if(name === 'news'){
            return this.$store.state.news;
        }else if(name === 'ask'){
            return this.$store.state.ask;
        }else if(name === 'jobs'){
            return this.$store.state.jobs;
        }
      }
  }
}
</script>

<style scoped>
.news-list{
  margin:0;
  padding:0;
}
.news-list .post{
  list-style:none;
  display:flex;
  align-items:center;
  border-bottom:1px solid #ddd;
}
.news-list .points{
  width:80px;
  height:60px;
  display:flex;
  justify-content:center;
  align-items:center;
  background-color:#eee;
}

.news-list .news-title{
  margin:0;
  padding:0 10px;
}
</style>