<!-- Posts.vue -->
<template>
    <div>
      <h2>Postingan</h2>
      <select v-model="selectedUser">
        <option v-for="user in users" :key="user.id" :value="user.id">{{ user.name }}</option>
      </select>
      <div v-if="selectedUser">
        <div v-for="post in filteredPosts" :key="post.id">
          <h3>{{ post.title }}</h3>
          <p>{{ post.body }}</p>
        </div>
      </div>
      <div v-else>
        <p>Silakan pilih pengguna untuk melihat postingan mereka.</p>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, computed, onMounted } from 'vue'
  
  const users = ref([]);
  const posts = ref([]);
  const selectedUser = ref(null);
  
  onMounted(() => {
    // Ambil data user dari API
    fetch('https://jsonplaceholder.typicode.com/users')
      .then(response => response.json())
      .then(data => {
        users.value = data;
      });
  
    // Ambil data postingan dari API
    fetch('https://jsonplaceholder.typicode.com/posts')
      .then(response => response.json())
      .then(data => {
        posts.value = data;
      });
  });
  
  const filteredPosts = computed(() => {
    // Filter postingan berdasarkan user yang dipilih
    return posts.value.filter(post => post.userId === parseInt(selectedUser.value));
  });
  </script>
  
  <style scoped>
  /* Add your styles here */
  </style>
  