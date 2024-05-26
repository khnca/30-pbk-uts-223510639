<!-- App.vue -->
<script setup>
import { ref } from 'vue'
import TodosInput from './components/TodosInput.vue'
import Posts from './components/Posts.vue'

const activeMenu = ref('todos');

const showTodos = () => {
  activeMenu.value = 'todos';
};

const showPosts = () => {
  activeMenu.value = 'posts';
};
</script>

<template>
  <div id="app">
    <!-- Header -->
    <header>
      <nav>
        <ul>
          <li @click="showTodos">Todos</li>
          <li @click="showPosts">Posts</li>
        </ul>
      </nav>
    </header>

    <!-- Main Content -->
    <main>
      <div v-if="activeMenu === 'todos'">
        <!-- Fitur Todos -->
        <h2>Todos</h2>
        <TodosInput />
      </div>
      <div v-else-if="activeMenu === 'posts'">
        <!-- Fitur Postingan -->
        <Posts />
      </div>
    </main>
  </div>
</template>

