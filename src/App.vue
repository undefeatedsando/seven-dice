<script setup>
import Dice from './components/Dice.vue'
import Result from './components/Result.vue'
import { reactive } from 'vue'

const diceArray = reactive([]);
let maxPoints = 7;
let diceSideNumber = 6;
const addDice = () => diceArray.push(rollDice())
const rollDice = () => Math.floor(Math.random() * diceSideNumber) + 1
const diceSum = () => diceArray.reduce((a, c) => a + c, 0)
const reset = () => diceArray.splice(0, diceArray.length)
</script>

<template>
  <h1>Your target is to get <input v-model="maxPoints"></h1>
  <h1>Dice has <input v-model="diceSideNumber"> sides</h1>
  <h1>Current score: {{ diceSum() }}</h1>
  <div class="roll-container">
     <TransitionGroup class="d-flex gap-3" tag="div" name="list">
     <div v-for="dice in diceArray" :key="dice">
         <Dice :value="dice"/>
     </div>
      
    </TransitionGroup>
  </div>
  
  <div class="container">
      <div class="align-center">
          <div class="btn btn-primary" @click="addDice()">Add dice</div>
          <div class="btn btn-outline-danger ms-3" @click="reset()">Reset</div>
      </div>
  </div>
  
  <Result v-if="diceSum() >= maxPoints" :expected="maxPoints" :actual="diceSum()"></Result>
</template>

<style scoped>
  .roll-container {
    display: flex;
    gap: 8px;
  }
  input {
    max-width: 2em;
  }
  .list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
</style>
