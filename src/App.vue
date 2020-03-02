<template>
  <div id="app">
    <div class="container mt-5">
      <div class="row align-items-center">
        <div class="col-md">
          <img src="./assets/img/calculator.svg" alt="Calculadora" width="500">
        </div>
        <div class="col-md">
          <h2 class="text-center">Bin2Dec</h2>
          <form-convert></form-convert>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css"
import "font-awesome/css/font-awesome.css"

import FormConvert from './components/FormConvert.vue'

export default {
  name: 'App',
  components: {
    FormConvert,
  }
}
</script>

<style>
  body {
    background: #f5f5f5;
  }

  .container, .align-items-center {
    height: 100vh;
  }
</style>
