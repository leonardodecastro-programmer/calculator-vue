<script setup>
import { setConstantValue } from 'typescript';
import { reactive } from 'vue';

  const state = reactive({
    plus: '-',
    result: '',
    filter: 'sum',
    input1: '0',
    input2: '0',
  })
  
  function execInput(x, event) {
    state.input1 = event.target.value
    calc()
  }

  const calc = () => {
    const { filter } = state;

    switch (filter) {
      case 'subtraction':
        state.result = parseFloat(state.input1) - parseFloat(state.input2);
        break
      case 'mutiplication':
        state.result = calcMutiplication();
        break
      case 'division':
        state.result = calcDivision();
      default:
        state.result = parseFloat(state.input1)  + parseFloat(state.input2);
    }
  }
</script>

<template>
  <div class="container vh-100 d-flex justify-content-center align-items-center">
      <select @change="event => state.filter = event.target.value" class="">
        <option value="sum">Sum</option>
        <option value="subtraction">Subtraction</option>
        <option value="mutiplication">Mutiplication</option>
        <option value="division">Division</option>
      </select>
      <input @keyup="execInput1" class="ms-2" type="text">
      <p class="ms-2">{{ }}</p>
      <input @keyup="execInput2" class="ms-2" type="text">
      <p class="ms-2">{{ state.result }}</p>
  </div>
</template>

<style scoped>
</style>