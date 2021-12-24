<template>
    <div class="container-fluid
                d-flex justify-content-center 
                align-items-center">
        <div class="card-form
                    shadow
                    border-0
                    rounded-3">
            <div class="bg-cep bg-white d-flex">
                <div class="container m-auto">
                    <div class="d-flex align-items-center justify-content-center">
                        <input class="form-control form-control-lg
                        w-50
                        shadow-sm"
                        type="text" placeholder="Digite o CEP">
                    </div>
                    <div class="row">
                        <button type="button" class="btn mt-3 w-25 mx-auto">Buscar</button>
                    </div>
                </div>
            </div>
           
        </div>
    </div>
</template>

<style>
.card-form{
    width: 800px;
    height: 500px;   
    /* background:  #00bdb4; */
}

.container-fluid {
    width: 100vw;
    height: 100vh;
       /* background: #00bdb4; */
    font-family: sans-serif;
   background: linear-gradient(179deg, rgba(19, 123, 155, 0.49) 0%, #4b8bc8 76%);
}

.bg-cep{
     width: 40%;
     height: 100%;
}

.btn {
    background: #4b8bc8 !important;
    color: white !important;
}


</style>


