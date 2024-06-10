<template>
    <div>
      <div class="row">
        <div class="col-md-6 mx-auto">
          <div class="mb-3">
            <label for="formGroupExampleDescription" class="form-label">Descrição</label>
            <input
              type="text"
              class="form-control"
              id="formGroupExampleDescription"
              v-model="description"
              placeholder="Descrição"
            />
          </div>
          <div class="mb-3">
            <label for="formGroupExampleInput2" class="form-label">Valor</label>
            <input
              type="number"
              class="form-control"
              id="formGroupExampleInput2"
              v-model="value"
              placeholder="R$"
            />
          </div>
          <div class="mb-3">
            <label for="formGroupExampleFile" class="form-label">Imagem do Produto</label>
            <input
              type="file"
              class="form-control"
              id="formGroupExampleFile"
              @change="onFileChange"
            />
          </div>
          <button @click="submit" class="btn btn-primary">Cadastrar produto</button>
        </div>
      </div>
  
      <div v-if="successMessage" class="alert alert-success mt-3" role="alert">
        {{ successMessage }}
      </div>
  
      <div class="cardteste">
        <div class="col-md-3 mx-auto">
          <!-- Adicionado mx-auto para centralizar o card -->
          <div class="card mb-3">
            <img
              v-if="selectedFile"
              :src="selectedFile"
              class="card-img-top"
              alt="Imagem do Produto"
              style="width: 100%;"
            />
            <div class="card-body">
              <p class="card-text">
                <strong>{{ description }}</strong>
              </p>
              <p class="card-text">
                <strong>R$ {{ value }}</strong>
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        description: "",
        value: 0,
        successMessage: "",
        selectedFile: null
      };
    },
    methods: {
      submit() {
        console.log("Produto cadastrado:", this.description, this.value);
        // Aqui você pode enviar a imagem junto com os outros dados para o backend
        // Exemplo: axios.post('/api/products', { description: this.description, value: this.value, image: this.selectedFile })
        this.successMessage = "Produto cadastrado com sucesso!";
        setTimeout(() => {
          this.successMessage = "";
        }, 3000); // Esconde a mensagem após 3 segundos
  
        // Limpar os campos após submissão
        this.description = "";
        this.value = 0;
        this.selectedFile = null;
      },
      onFileChange(event) {
        const file = event.target.files[0];
        this.selectedFile = URL.createObjectURL(file);
      }
    }
  };
  </script>
  
  <style scoped>
  .cardteste {
    margin-top: 20px;
    display: flex;
    justify-content: center; /* Centraliza horizontalmente */
  }
  .card {
    border-radius: 5px;
  }
  .card-body {
    background-color: #fff;
    color: #000;
  }
  .card-text {
    text-align: center;
  }
  </style>
  