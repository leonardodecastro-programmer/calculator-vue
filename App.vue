<!-- 
  [B] 1 - criar template
  [B] 2 - exibir input 0
  [B] 3 - clicar no botão somar exibir a soma com sinal da operação
  4 - atualizar resultado ao clicar no sinal da operação
-->
<script setup>
  import { reactive } from 'vue';

  const state = reactive ({
    currentNumber: '0',
    result: 0,
  })

  function addDigit(d) {
    if(state.currentNumber == '0' ) {
      state.currentNumber = d
    } else {
      state.currentNumber += d
    }
    calcSum()
  }

  function calcSum() {
    state.result = parseFloat(state.currentNumber)
    state.currentNumber = state.result
  }
</script>

<template>
  <div class="container vh-100 d-flex justify-content-center align-items-center">
      <div class="calculator border rounded p-3 pb-1">
          <div class="input d-flex justify-content-end align-items-end flex-column">
            <p class="mb-1">{{ state.result == 0  ? '' : `${state.result}+` }}</p>
            <p class="text-end">{{ state.currentNumber }}</p>
          </div>
          <div class="row">
              <button class="col mb-1 btn btn-secondary">%</button>
              <button class="col mb-1 mx-1 btn btn-secondary">CE</button>
              <button class="col mb-1 mx-1 btn btn-secondary">C</button>
              <button class="col mb-1 mx-1 btn btn-secondary"><i class="bi bi-arrow-left-square"></i></button>
          </div>
          <div class="row">
              <button class="col mb-1 btn btn-secondary"><sup>1</sup>/<sub>x</sub></button>
              <button class="col mb-1 mx-1 btn btn-secondary">x<sup>2</sup></button>
              <button class="col mb-1 mx-1 btn btn-secondary">√</button>
              <button class="col mb-1 mx-1 btn btn-secondary">÷</button>
          </div>
          <div class="row">
              <button @click="addDigit('7')" class="col mb-1 btn btn-light">7</button>
              <button @click="addDigit('8')" class="col mb-1 mx-1 btn btn-light">8</button>
              <button @click="addDigit('9')" class="col mb-1 mx-1 btn btn-light">9</button>
              <button class="col mb-1 mx-1 btn btn-secondary">x</button>
          </div>
          <div class="row">
              <button @click="addDigit('4')" class="col mb-1 btn btn-light">4</button>
              <button @click="addDigit('5')" class="col mb-1 mx-1 btn btn-light">5</button>
              <button @click="addDigit('6')" class="col mb-1 mx-1 btn btn-light">6</button>
              <button class="col mb-1 mx-1 btn btn-secondary">-</button>
          </div>
          <div class="row">
              <button @click="addDigit('1')" class="col mb-1 btn btn-light">1</button>
              <button @click="addDigit('2')" class="col mb-1 mx-1 btn btn-light">2</button>
              <button @click="addDigit('3')" class="col mb-1 mx-1 btn btn-light">3</button>
              <button @click="calcSum()" class="col mb-1 mx-1 btn btn-secondary">+</button>
          </div>
          <div class="row">
              <button class="col btn btn-light"><sup>+</sup>/<sub>-</sub></button>
              <button @click="addDigit('0')" class="col mx-1 btn btn-light">0</button>
              <button class="col mx-1 btn btn-light">.</button>
              <button class="col mx-1 btn btn-primary">=</button>
          </div>
      </div>
    </div>
</template>

<style scoped>
  .input {
    min-height: 70px;
  }
</style>