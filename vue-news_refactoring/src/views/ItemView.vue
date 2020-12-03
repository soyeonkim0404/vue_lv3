<template>
  <div>
    <section>
        <router-link :to="`/user/${itemInfo.user}`">{{ itemInfo.user }}</router-link>
        <div>{{ itemInfo.time_ago }}</div>
        <h2>{{ itemInfo.title }}</h2> 
        <div v-html="itemInfo.content"></div>
    </section>
  </div>
</template>

<script>
export default {
    computed:{
        itemInfo(){
            return this.$store.state.item;
        }
    },
    created() {
        const askItem = this.$route.params.id;
        this.$store.dispatch('FETCH_ITEM', askItem);
    }
}
</script>

<style>

</style>