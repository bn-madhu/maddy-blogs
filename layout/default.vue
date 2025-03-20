<template>
    <div>
      <header>
        <h1>My Nuxt.js Blog</h1>
      </header>
      <main>
        <nuxt />
      </main>
      <footer>
        <p>&copy; 2025 My Blog</p>
      </footer>
    </div>
  </template>
  
  <style scoped>
    header {
      background-color: #333;
      color: white;
      padding: 1rem;
      text-align: center;
    }
    footer {
      background-color: #333;
      color: white;
      text-align: center;
      padding: 1rem;
      position: absolute;
      bottom: 0;
      width: 100%;
    }
  </style>