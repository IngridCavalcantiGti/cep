<template>
  <div class="form container-fluid d-flex justify-content-center 
                align-items-center">
    <FormCep/>
  </div>
</template>

<script>
import  {  defineComponent } from  '@vue/composition-api'
import FormCep from '@/components/FormCep.vue'

export  default  defineComponent ( { 
  name: 'Home',
  components: {
    FormCep
  },

})

</script>

<style>
.container-fluid {
    width: 100vw;
    height: 100vh;
       /* background: #00bdb4; */
   background: linear-gradient(179deg, rgba(19, 123, 155, 0.49) 0%, #4b8bc8 76%);
}
</style>