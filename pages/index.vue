<template>
  <div id="app">
    <div v-for="post in posts" :key="post.id">
      {{ post.message }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: null,
    };
  },
  async created() {
    this.posts = await this.$strapi.$posts.find();
  },
};
</script>
