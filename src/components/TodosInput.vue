<!-- TodosInput.vue -->
<template>
    <section class="create-todo">
      <form id="new-todo-form" @submit.prevent="addTodo">
        <h4>LIST AKTIVITAS</h4>
        <input 
          type="text" 
          name="content" 
          id="content" 
          placeholder="Ketik Disini"
          v-model="input_content" 
        />
        <h4>WAKTU</h4>
        <div class="options">
          <label>
            <input 
              type="radio" 
              name="category" 
              id="category1" 
              value="Harian"
              v-model="input_category" 
            />
            <span class="bubble Harian"></span>
            <div>Harian</div>
          </label>
          <label>
            <input 
              type="radio" 
              name="category" 
              id="category2" 
              value="Kuliah"
              v-model="input_category" 
            />
            <span class="bubble Kuliah"></span>
            <div>Kuliah</div>
          </label>
        </div>
        <input type="submit" value="add Todo" />
      </form>
    </section>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const input_content = ref('')
  const input_category = ref(null)
  
  const addTodo = () => {
    if (input_content.value.trim() === '' || input_category.value === null) {
      return
    }
  
    todos.value.push({
      content: input_content.value,
      category: input_category.value,
      done: false,
      editable: false,
      createdAt: new Date().getTime()
    })
  
    input_content.value = ''
    input_category.value = null
  }
  </script>
  
  <style scoped>
  /* Add your styles here */
  </style>
  