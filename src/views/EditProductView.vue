<template>
    <div>
      <h2>Editar Produto</h2>
      <form @submit.prevent="updateProduct">
        <div class="mb-3">
          <label for="description" class="form-label">Descrição</label>
          <input type="text" class="form-control" id="description" v-model="product.description" />
        </div>
        <div class="mb-3">
          <label for="value" class="form-label">Valor</label>
          <input type="number" class="form-control" id="value" v-model="product.value" />
        </div>
        <button type="submit" class="btn btn-primary">Salvar</button>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        productId: null,
        product: {
          description: '',
          value: 0
        }
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
      updateProduct() {
        axios.put(`https://api.example.com/products/${this.productId}`, this.product)
          .then(response => {
            console.log('Produto atualizado com sucesso:', response.data);
          })
          .catch(error => {
            console.error('Erro ao atualizar produto:', error);
          });
      }
    }
  };
  </script>
  
  <style>
  /* Estilos opcionais */
  </style>
  