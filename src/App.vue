<template>
   <div id="app">
    <Calculator></Calculator>
  </div>
</template>


<script>
import Calculator from './components/Calculator.vue'
export default {
  name: 'App',
  components: {
    Calculator
  }
}
</script>



<style scoped>
  body {
    background: #31475e !important;
  }
</style>
