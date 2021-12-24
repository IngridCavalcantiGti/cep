<template>
  <div class="form">
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