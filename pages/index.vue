<template>
    <div>
      <h2>Blog Posts</h2>
      <ul>
        <li v-for="post in posts" :key="post.slug">
          <nuxt-link :to="`/post/${post.slug}`">{{ post.title }}</nuxt-link>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    async asyncData({ $content }) {
      const posts = await $content('posts').fetch();
      return { posts };
    },
  };
  </script>
  