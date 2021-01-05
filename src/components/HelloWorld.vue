<template>
  <div class="test-component">
    <div class="post" v-for="post in posts">
      <span class="post__id">{{ post.id }}</span>
      <span class="post__title">{{ post.title }}</span>
    </div>
    <v-btn @click="loadPosts">Load posts</v-btn>
    <v-btn @click="posts = []">Clear posts</v-btn>
  </div>
</template>

<script>
  const fs = require("fs");
  const { dialog } = require("electron").remote;

  export default {
    name: 'HelloWorld',

    data: () => ({
      posts : []
    }),
    created() {
      this.loadPosts();
    },
    methods: {
      loadPosts() {
        this.$axios
            .get('https://my-json-server.typicode.com/typicode/demo/posts')
            .then(({ data }) => this.posts = data)
      }
    }
  }
</script>
