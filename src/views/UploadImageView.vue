<template>
    <div id="app">
      <ImageUpload />
    </div>
  </template>
  
  <script>
  import ImageUpload from '../components/UploadComponents.vue';
  
  export default {
    name: 'App',
    components: {
      ImageUpload
    }
  };
  </script>
  
  <style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  </style>
  