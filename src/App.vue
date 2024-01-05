<script setup>
import { reactive } from 'vue';

  const state = reactive({
    plus: '',
    result: '',
    filter: 'sum',
    input1: '30',
    input2: '',
  })

  function calcSum() {
    return state.result =  state.input1 + state.input2
  }

  function calcSubtraction() {
    return state.result =  state.input1 - state.input2
  }

  function calcMutiplication() {
    return state.result =  state.input1 * state.input2
  }

  function calcDivision() {
    return state.result =  state.input1 / state.input2
  }

  const getSetCalc = () => {
    const { filter } = state;
    let setCalc;

    switch (filter) {
      case 'subtraction':
        return setCalc = calcSubtraction();
      case 'mutiplication':
        return setCalc = calcMutiplication();
      case 'division':
        return setCalc = calcDivision();
      default:
        return setCalc = calcSum();
    }
  }
  console.log(state.input2)
</script>

<template>
  <div class="container vh-100 d-flex justify-content-center align-items-center">
      <select @change="event => state.filter = event.target.value" class="">
        <option value="sum">Sum</option>
        <option value="subtraction">Subtraction</option>
        <option value="mutiplication">Mutiplication</option>
        <option value="division">Division</option>
      </select>
      <input :value="state.input1" class="ms-2" type="text">
      <p class="ms-2">{{ state.plus }}</p>
      <input :value="state.input2" class="ms-2" type="text">
      <p class="ms-2">{{ state.result }}</p>
  </div>
</template>

<style scoped>
</style>