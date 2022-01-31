## Create Nuxt Project
`yarn create nuxt-app <project-name>`

## Add Strapi Module
`yarn add @nuxtjs/strapi@^0.3.1`

## Then, add @nuxtjs/strapi to the modules section of nuxt.config.js:

```javascript
export default {
  modules: ['@nuxtjs/strapi'],
  strapi: {
    url: 'http://localhost:1337',
    entities: ['posts']
  }
}
```

## Create Strapi Project (version 3.10 ee) NPM

`npx create-strapi-app@ee backend`

## Add to /frontend/index.vue

```vue  
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
```

```vue
<template>
  <div id="app">
    <div v-for="post in posts" :key="post.id">
      {{ post.message }}
    </div>
  </div>
</template>
```