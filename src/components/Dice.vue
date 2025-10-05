<script setup>
import { ref } from 'vue'

defineProps({
  value: Number,
})

const count = ref(0)
</script>

<template>
  <h1 class="dice">{{ value }}</h1>
</template>

<style scoped>
    .dice {
        border: 1px solid black;
        width: 100px;
        height: 100px;
        border-radius: 30px;
        line-height: 1.8em;
    }
</style>
