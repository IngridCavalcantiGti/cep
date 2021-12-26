<template>
  <div class="card-form shadow border-0 rounded-3 d-flex">
    <div class="bg-white d-flex">
      <div class="container m-auto">
        <div class="d-flex align-items-center justify-content-center">
          <input
            class="form-control form-control-lg shadow-sm"
            type="text"
            placeholder="Digite o CEP"
            v-model="cep"
            
          />
        </div>
        <div class="row">
          <button type="button" @click="searchCep" class="btn mt-3 mx-auto">
            Buscar
          </button>
        </div>
      </div>
    </div>
    <div class="bg-form p-3 m-auto">
      <ul class="list-group list-group-flush">
        <span class="d-flex mb-2">
          <li class="list-group-item w-75">Logradouro</li>
          <li class="list-group-item w-25 ms-1">N</li>
        </span>

        <li class="list-group-item mb-2">Cidade</li>
        <li class="list-group-item mb-2">Bairro</li>
        <span class="d-flex">
          <li class="list-group-item mb-2 w-50">UF</li>
          <li class="list-group-item mb-2 w-50 ms-1">DDD</li>
        </span>
      </ul>
       <pre>{{ data }}</pre>  <!--   testando o resultado -->
    </div>
   
  </div>
</template>
<script>
import { defineComponent,  ref } from "@vue/composition-api";
import axios from "axios";

export default defineComponent({
  setup() {
      const data = ref(null);
      const cep = ref(null)
 
       const searchCep = () => {
        const getCep = cep.value
        axios.get(`https://viacep.com.br/ws/${getCep}/json/`)
          .then(response => 
           data.value = response.data
          )
          .catch(error => console.log(error))
      }

  return { searchCep, data, cep };
  }
});
</script>

<style>
.card-form {
  width: 800px;
  height: 500px;
}

.bg-cep {
  width: 40%;
  height: 100%;
}

.bg-form {
  width: 80%;
  height: 100%;
}

.btn {
  background: #4b8bc8 !important;
  color: white !important;
  width: 30% !important;
}

.form-control {
  width: 70% !important;
}
</style>
