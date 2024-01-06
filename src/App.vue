<!-- 
  [P] not NaNumber
  [P] render plus active switch
  switch calc real time
  design
-->

<script setup>
import { setConstantValue } from 'typescript';
import { reactive } from 'vue';

  const state = reactive({
    operation: '+',
    result: '',
    filter: 'sum',
    input1: '0',
    input2: '0',
  })

  function changeOperation(event) {
    state.filter = event.target.value
    state.operation = event.target.value
  }
  
  function execInput(event) {
    if(event.target.id === 'input1') {
      state.input1 = event.target.value
    }else {
      state.input2 = event.target.value
    }
    if(state.input1 === '') {
      state.input1 = 0
      state.input1 - state.input2
    } else if(state.input2 === '') {
      state.input2 = 0
      state.input1 - state.input2
    }
    calc()
  }

  

  const calc = () => {
    const { filter } = state;

    switch (filter) {
      case 'subtraction':
        state.result = parseFloat(state.input1) - parseFloat(state.input2);
        break
      case 'mutiplication':
        state.result = parseFloat(state.input1) * parseFloat(state.input2);
        break
      case 'division':
        state.result = parseFloat(state.input1) / parseFloat(state.input2);
      default:
        state.result = parseFloat(state.input1)  + parseFloat(state.input2);
    }
  }
</script>

<template>
  <div class="container vh-100 d-flex justify-content-center align-items-center">
      <select @change="changeOperation" class="">
        <option value="+">Sum</option>
        <option value="-">Subtraction</option>
        <option value="x">Mutiplication</option>
        <option value="/">Division</option>
      </select>
      <input id="input1" @keyup="execInput" value="" class="ms-2" type="text">
      <p class="ms-2">{{ state.operation }}</p>
      <input id="input2" @keyup="execInput" class="ms-2" type="text">
      <p class="ms-2">{{ state.result }}</p>
  </div>
</template>

<style scoped>
</style>