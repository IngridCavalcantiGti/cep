<template>
  <div class="container-fluid">
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
   background: linear-gradient(179deg, rgba(12, 12, 12, 0.98) 6%, #414141 100%);
}

</style>