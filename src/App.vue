<!-- 
  [P] start with input enter none and result none
  [P] not be NaN
  style
-->
<script setup>
  import { setConstantValue } from 'typescript';
  import { reactive } from 'vue';

  const state = reactive({
    values: { value1: 0, value2: 0 },
    selectedOperation: 'add',
  });

  const updateOperation = (event) => {
    state.selectedOperation = event.target.value;
  };

  const updateValue1 = (event) => {
    state.values.value1 = event.target.value;
  };

  const updateValue2 = (event) => {
    state.values.value2 = event.target.value;
  };

  const calculateResult = () => {
    if(state.values.value1 !== '' && state.values.value2 !== '') {
      const num1 = parseFloat(state.values.value1);
      const num2 = parseFloat(state.values.value2);

      switch (state.selectedOperation) {
        case 'add':
          return num1 + num2;
        case 'subtract':
          return num1 - num2;
        case 'multiply':
          return num1 * num2;
        case 'divide':
          return num2 !== 0 ? num1 / num2 : 'Infinito';
        default:
          return 0;
      }
    } else {
      return
    }
  };

</script>

<template>
  <div class="container vh-100 d-flex justify-content-center align-items-center">
      <div class="container-color p-2 d-flex flex-column align-items-center rounded-2">
          <div class="result-container bg-secondary w-100 mb-2 rounded-2">
            <p class="result text-center m-0">{{ calculateResult() }}</p>
          </div>
          <select @change="changeOperation" class="w-100 mb-2 form-select">
            <option value="+">Sum</option>
            <option value="-">Subtraction</option>
            <option value="x">Mutiplication</option>
            <option value="/">Division</option>
          </select>
          <input class="w-100 mb-2 form-control bg-light" value="" type="number" @keyup="updateValue1">
          <input class="w-100 mb-2 form-control bg-light" value="" type="number" @keyup="updateValue2">
      </div>
  </div>
</template>

<style>

  .container-color {
    background-color: rgb(20, 20, 20);
  }

  .result {
    height: 60px;
  }

  .result {
    line-height: 60px;
  }
  select {
    background-color: rgb(202, 131, 0) !important;
    border: none !important;
    padding: 10px;
  }
  input[type="text"] {
    background-color: #e9e9e9 !important;
    border: none !important;
  }
</style>