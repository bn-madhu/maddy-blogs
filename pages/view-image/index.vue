<template>
    <div>
      <header>
        <h1>Blog Post with Image</h1>
        <input v-model="searchQuery" type="text" placeholder="Search posts..." />
      </header>
  
      <div class="image-section">
        <img src="https://via.placeholder.com/800x400" alt="Blog Image" />
        <h2>Blog Post Title</h2>
      </div>
  
      <div class="post-content">
        <p>Here is some content for the blog post. You can add more details here about your post. The search bar above allows users to search for blog posts by title.</p>
      </div>
  
      <div v-if="filteredPosts.length > 0" class="search-results">
        <h3>Search Results:</h3>
        <ul>
          <li v-for="post in filteredPosts" :key="post.slug">
            <nuxt-link :to="`/post/${post.slug}`">{{ post.title }}</nuxt-link>
          </li>
        </ul>
      </div>
      <div v-else class="no-results">
        <p>No posts found.</p>
      </div>

      <div v-if="filteredPosts.length > 0" class="posts-list">
        <div v-for="post in filteredPosts" :key="post.slug" class="post-item">
            <img :src="post.image" :alt="post.title" />
            <div>
            <h2>{{ post.title }}</h2>
            <p>{{ post.description }}</p>
            <nuxt-link :to="post.slugUrl">Read More</nuxt-link>
            </div>
        </div>
        </div>

        <div v-else class="no-results">
        <p>No posts found.</p>
        </div>

    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        searchQuery: "",
        posts: [
          { title: "My First Blog Post", slug: "my-first-post" },
          { title: "Another Blog Post", slug: "another-blog-post" },
          { title: "A Third Blog Post", slug: "third-blog-post" },
        ],
        images:[]
      };
    },
    async asyncData({ $content }) {
        // Fetch posts from the content/posts directory
        const posts = await $content('imagePost').fetch();
        return { posts };
    },
    computed: {
      filteredPosts() {
        return this.posts.filter((post) =>
          post.title.toLowerCase().includes(this.searchQuery.toLowerCase())
        );
      },
    },
  };
  </script>
  
  <style scoped>
  header {
    text-align: center;
    margin: 20px;
  }
  
  input {
    padding: 10px;
    font-size: 16px;
    margin-top: 10px;
    width: 80%;
  }
  
  .image-section {
    text-align: center;
    margin-top: 30px;
  }
  
  .image-section img {
    max-width: 100%;
    height: auto;
  }
  
  h2 {
    font-size: 24px;
    margin-top: 15px;
  }
  
  .post-content {
    margin-top: 30px;
  }
  
  .search-results {
    margin-top: 20px;
  }
  
  .no-results {
    color: red;
  }
  </style>  