<template>
    <div>
      <h2>Upload de Imagem</h2>
      <input type="file" @change="onFileChange">
      <button @click="uploadImage">Upload</button>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        selectedFile: null
      };
    },
    methods: {
      onFileChange(event) {
        this.selectedFile = event.target.files[0];
      },
      uploadImage() {
        let formData = new FormData();
        formData.append('foto', this.selectedFile);
  
        axios.post('https://localhost:5001/imagens/upload', formData, {
          headers: {
            'Content-Type': 'multipart/form-data'
          }
        })
        .then(response => {
          console.log('Upload bem-sucedido:', response);
        })
        .catch(error => {
          console.error('Erro no upload:', error);
        });
      }
    }
  };
  </script>
  
  <style scoped>
  h2 {
    margin-bottom: 20px;
  }
  input {
    margin-right: 10px;
  }
  </style>
  