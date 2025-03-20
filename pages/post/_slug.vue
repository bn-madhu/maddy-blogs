<!-- <template>
    <div>
      <h2>{{ post.title }}</h2>
      <p>{{ post.date }}</p>
      <div v-html="post.body"></div>
    </div>
  </template>
  
  <script>
  export default {
    async asyncData({ $content, params }) {
      const post = await $content('posts', params.slug).fetch();
      return { post };
    },
  };
  </script>   -->


  <template>
    <div>
      <header>
        <h1>{{ post.title }}</h1>
      </header>
  
      <div class="post-content">
        <img :src="post.image" :alt="post.title" />
        <p>{{ post.description }}</p>
        <div v-html="post.body"></div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    async asyncData({ $content, params }) {
      // Fetch the post based on its slug
      const post = await $content('posts', params.slug).fetch();
      return { post };
    },
  };
  </script>
  
  <style scoped>
  .post-content img {
    width: 100%;
    height: auto;
  }
  
  h1 {
    text-align: center;
    margin-top: 30px;
  }
  
  .post-content {
    padding: 20px;
  }
  </style>
  