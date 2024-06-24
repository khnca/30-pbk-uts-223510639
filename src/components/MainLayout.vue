<template>
    <q-layout view="hHh lpR fFf">
      <q-header elevated class="bg-soft-pink text-white">
        <q-toolbar class="custom-toolbar">
          <q-toolbar-title class="custom-toolbar-title">
            Nadia Khalisah Khansa | UAS2 PBK
          </q-toolbar-title>
          <div class="toolbar-tabs-container">
            <q-tabs class="toolbar-tabs">
              <q-route-tab to="/Todo" label="ToDo List" />
              <q-route-tab to="/Post" label="Post" />
              <q-route-tab to="/Album" label="Album" />
            </q-tabs>
          </div>
        </q-toolbar>
      </q-header>
  
      <q-page-container>
        <router-view />
      </q-page-container>
    </q-layout>
  </template>
  
  <script>
  import { ref } from "vue";
  
  export default {
    setup() {
      const leftDrawerOpen = ref(false);
  
      return {
        leftDrawerOpen,
        toggleLeftDrawer() {
          leftDrawerOpen.value = !leftDrawerOpen.value;
        },
      };
    },
  };
  </script>
  
  <style scoped>
  .custom-toolbar {
    padding: 20px;
    display: flex;
    align-items: flex-end;
  }
  
  .custom-toolbar-title {
    font-size: 2.5rem;
    flex-grow: 1;
    font-family: 'Pacifico', cursive; 
    color: #fff;
  }
  
  .toolbar-tabs-container {
    display: flex;
    align-items: flex-end;
  }
  
  .toolbar-tabs {
    margin-left: auto;
  }
  
  .bg-soft-pink {
    background-color: #fc8bba;
  }
  
  @import url('https://fonts.googleapis.com/css2?family=Pacifico&display=swap');
  </style>
  