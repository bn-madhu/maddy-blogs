<template>
  <div>
    <!-- Global Search Bar -->
    <header>
      <input 
        v-model="searchQuery" 
        type="text" 
        placeholder="Search posts..." 
        class="search-input"
      />
    </header>

    <!-- <NuxtRouteAnnouncer />
    <NuxtWelcome /> -->
    <Nuxt />
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: "",
    };
  },
  watch: {
    // You can watch for search query change to do additional tasks globally
    searchQuery(newQuery) {
      this.$root.$emit("searchQueryChanged", newQuery);
    },
  },
};
</script>

<style scoped>
.search-input {
  padding: 10px;
  font-size: 16px;
  width: 300px;
  margin: 20px auto;
  display: block;
}
</style>
