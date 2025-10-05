<script setup>
import { ref } from 'vue'

defineProps({
  expected: Number,
  actual: Number,
})

const percent = (actual, expected) => {
    return Math.floor((actual / expected - 1) * 100)
}
</script>
  
<template>
    <h2 class="mt-3">Check finished!</h2>
    <h2 class="mt-3 text-success">Obtained {{expected}} points <span v-if="actual === expected">PERFECT SCORE</span></h2>
    <h2 class="mt-3 text-danger" v-if="actual !== expected">Obtained {{ actual - expected }} problem points ({{percent(actual, expected)}}%)</h2>
</template>