<template>
    <div>
      <h2>Excluir Produto</h2>
      <p>Tem certeza que deseja excluir o produto "{{ product.description }}"?</p>
      <button @click="deleteProduct" class="btn btn-danger">Excluir</button>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        productId: null,
        product: null
      };
    },
    mounted() {
      this.productId = this.$route.params.id; 
      this.fetchProductDetails();
    },
    methods: {
      fetchProductDetails() {
        axios.get(`https://api.example.com/products/${this.productId}`)
          .then(response => {
            this.product = response.data;
          })
          .catch(error => {
            console.error('Erro ao buscar detalhes do produto:', error);
          });
      },
      deleteProduct() {
        if (confirm(`Tem certeza que deseja excluir o produto "${this.product.description}"?`)) {
          axios.delete(`https://api.example.com/products/${this.productId}`)
            .then(response => {
              console.log('Produto excluído com sucesso:', response.data);
            })
            .catch(error => {
              console.error('Erro ao excluir produto:', error);
            });
        }
      }
    }
  };
  </script>
  
  <style>
  </style>
  