<template>
  <div>
   <div class="card">
     <div class="card-body">
       <div class="form-group">
        <b>Binário</b>
        <input type="text" maxlength="8" v-model="binary" class="form-control" v-bind:class="[this.error ? 'is-invalid' : '']" v-on:keyup.enter="convert()" v-on:keyup="validate()" placeholder="Digite o número em binário...">
        <div class="invalid-feedback">
          O dígito precisa ser 0 ou 1
        </div>
       </div>
       <div class="form-group">
         <button class="btn btn-primary btn-lg btn-block" @click="convert()">Converter <i class="fa fa-arrow-right"></i></button>
       </div>
       <div class="form-group">
         <b>Decimal</b>
         <input type="text" v-model="decimal" class="form-control" readonly>
       </div>
     </div>
   </div>
  </div>
</template>

<script>
export default {
  name: 'FormConvert',
  data() {
    return {
      error: false,
      binary: '',
      decimal: 0,
    }
  },
  methods: {
    convert() {
      this.decimal = 0;
      for(let i = this.binary.length-1; i >= 0; i--) {
        this.decimal += parseInt(this.binary[i]) * Math.pow(2, this.binary.length-1-i);
        console.log(`${parseInt(this.binary[i])} * ${Math.pow(2, this.binary.length-1-i)}`);
      }

      this.binary = '';
    },
    validate() {
      if(this.binary.length === 8) {
        return;
      }

      let key = window.event.key;
      (key !== '0' && key !== '1' && key !== 'Backspace' && key !== 'Tab' && key !== 'Enter') ? this.error = true : this.error = false;

      if(key === 'Backspace' ) {
        const keyword = this.binary.substr(this.binary.length-1, 1);
        (keyword !== '0' && keyword !== '1' && this.binary.length > 0) ? this.error = true : this.error = false;
      }
    }
  }
}
</script>

<style scoped>

</style>
