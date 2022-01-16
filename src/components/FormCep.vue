<template>     
  <div class="container-fluid d-grid">
    <div class="align-self-center">
      <div class="row d-flex justify-content-center">
        <div class="col-3">
            <div class="input-group  rounded-pill box-cep">
          <input type="text" class="form-control input-cep text-white custom-input" placeholder="Busca CEP" v-model="cep" >
          <button class="btn btn-outline-secondary" type="button" @click="searchCep"><i class="bi-search text-light"></i></button>
        </div>
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
      <div class="row  d-flex justify-content-center mt-5 ">
        <div class="col-5">
          <input id="city" class="form-control input-back text-white custom-input" type="text"  v-model="data.localidade" readonly />
        </div>
        <div class="col-5 ms-5">
         <input id="district" class="form-control input-back text-white custom-input" type="text"  v-model="data.uf" readonly/>
        </div>
      </div>
    </div>
  
    <div>
      <span class="text-white footer my-auto col-3"></span> 
      <span class="text-white my-auto col-3 ms-2">Consulta de endereço pelo CEP</span> 
      <span class="text-white footer my-auto col-3 ms-2"></span> 
    </div>
    
   </div>
</template>

<script>
import { defineComponent,  ref } from "@vue/composition-api";
import axios from "axios";

export default defineComponent({
  setup() {
      const data = ref('');
      const cep = ref(null)
 
       const searchCep = () => {
        
        const getCep = cep.value

        axios.get(`https://viacep.com.br/ws/${getCep}/json/`)
          .then(response => 
           data.value = response.data
          
          )
          .catch(error => console.log(error))
      }

  return { searchCep, data, cep,  };
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

  button {
    background:  #26a69a !important;
    border-radius: 50% !important;
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
</style>
