<template>     
  <div class="container-fluid d-grid align-content-center">
    <div class="align-self-center">
      <div class="row d-flex justify-content-center">
        <div class="col-3 h-64">
            <div class="input-group rounded-pill box-cep" :class="{ 'border border-danger': hasError }">
              <input type="text" class="form-control input-cep text-white custom-input " v-mask="'#####-###'" placeholder="Busca CEP" v-model="cep" @keyup.enter="searchCep">
              <button class="btn btn-outline-secondary" type="button" @click="searchCep"><i class="bi-search text-light"></i></button>
           </div>
            <span class="text-danger ms-3 small" v-if="hasError">Cep não encontrado</span>
        </div>
      </div>
       <div class="row mt-5 d-flex justify-content-center">
          <div class="col-5">
            <input id="name" class="form-control input-back text-white custom-input" type="text"  v-model="data.logradouro" readonly />
          </div>
          <div class="col-5 ms-5">
             <input id="district" class="form-control input-back text-white custom-input" type="text"  v-model="data.bairro" readonly />
          </div>
      </div>
      <div class="row d-flex justify-content-center mt-5 ">
        <div class="col-5">
            <input id="city" class="form-control input-back text-white custom-input" type="text"  v-model="data.localidade" readonly />
        </div>
        <div class="col-5 ms-5 text-white">
            <input id="district" class="form-control input-back text-white custom-input" type="text"  v-model="data.uf" readonly/>
         <div class="d-flex justify-content-end mt-5">
            <button class="btn custom  text-white" @click='clear'>Limpar </button>
          </div>
        </div>
      </div> 
    </div>
        <div class="d-flex justify-content-start ">
          <div>
            <span class="text-white footer my-auto"></span> 
            <span class="text-white my-auto ms-2">Consulta de endereço pelo CEP</span> 
            <span class="text-white footer my-auto ms-2"></span>
          </div>
        </div>
   </div>
</template>

<script>
import { defineComponent,  ref } from "@vue/composition-api";
import axios from "axios";

export default defineComponent({
  setup() {
      const data = ref('');
      const cep = ref(null);
      const hasError = ref(false);
         
      const searchCep = () => {
      const getCep = cep.value;
      const formatCep = getCep.replace('-', '')
     
        if(formatCep.length === 8) {
            axios.get(`https://viacep.com.br/ws/${formatCep}/json/`)
            
            .then(response =>  data.value = response.data )
            .then(() =>   { 
                if(Object.keys(data.value)[0] === 'erro') { 
                  hasError.value = true;
                } else {
                   hasError.value = false;
                }
              })
            .catch(error => console.log(error))
        }
      }

       const clear = () => {data.value = '', cep.value = '', hasError.value = false}

      return { searchCep, data, cep, clear, hasError};
  }
});
</script>

<style>

  .input-back{
    background: transparent !important;
    border-top: none !important;
    border-left: none !important;
    border-right: none !important;
    border-bottom: 1px solid  #26a69a !important;;
  }
  
  .input-cep{
    background: transparent !important;
    border:none !important;
  }

  button:not(.custom) {
    background:  #26a69a !important;
    border-radius: 50% !important;
  }

  button:hover {
    background:  #1d8177 !important;
  }

  .box-cep{
    background: gradiente;
    border:none !important
  }

  .input-group {
    border-radius: 20px !important;
    background: linear-gradient(180deg, rgba(255, 255, 255, 0.15), rgba(255, 255, 255, 0));
  }

 .custom-input:focus {
  outline: none !important;
  box-shadow: none !important;;
   box-shadow: none !important;
}

.footer{ 
  padding-right: 20px;
  background: #26a69a;
}

.custom {
   border-radius: 5px !important;
    background: #26a69a !important;
}

.h-64 {
  height: 64px;
}
</style>
