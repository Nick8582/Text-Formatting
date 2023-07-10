<template>
  <div class="container">
    <ul class="list">
      <ThePost v-for="(data, index) in postsParse" :key="index" :data="data"/>
    </ul>
  </div>
</template>

<script>
import ThePost from "./Post/ThePost.vue";
import dataPosts from "../assets/feed.json"

export default {
  name: 'TheMain',
  components: {ThePost},
  data() {
    return {
      posts: dataPosts,
    }
  },
  computed: {
    postsParse() {
      return this.posts.map(dataSet => dataSet)
    },
  }
}
</script>

<style>
.container {
  max-width: 1000px;
  margin: 0 auto;
}

.list {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>
