<template>
  <li class="item">
    <div>{{localeTime}}, {{localeDate}} / <a class="link__author" :href="data.authorUrl" target="_blank">{{data.authorName}} / {{data.authorUrl}}</a> </div>
    <div>
      <TextPost :text="data.content" :textTones="data.contentPostTones" />
    </div>
  </li>
</template>

<script>
import TextPost from "./TextPost.vue";
export default {
  components: {TextPost},
  props: ['data'],
  name: "ThePost",
  computed: {
    localeTime() {
      return(
          new Date(this.data.date).toLocaleTimeString()
      )
    },
    localeDate() {
      return(
          new Date(this.data.date).toLocaleDateString()
      )
    },
  }
}
</script>

<style>
.item {
  border-radius: 10px;
  padding: 10px;
  transition: box-shadow .3s ease-in-out;
  cursor: pointer;
}

.item:not(:last-child) {
  margin-bottom: 10px;
}

.item:hover {
  box-shadow: 0 0 10px #000;
}
.link__author {
  color: #00569a;
  text-decoration: none;
}
</style>
