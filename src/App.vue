<template>
  <div id="app">
      <router-view/>
  </div>
</template>

<script>
import { defineComponent } from '@vue/composition-api'
import FormCep from '@/components/FormCep.vue'


export default defineComponent({
  components: {
    FormCep
  },
  setup() {
    
  },
})
</script>

