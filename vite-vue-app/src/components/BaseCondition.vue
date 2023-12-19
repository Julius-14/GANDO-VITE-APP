<script setup>
import { ref } from 'vue';

let numbers = ref([
    "a",
    "b",
    "c",
    "d",
    "e",
])
console.log('test')
</script>
<template>
    <p v-for="(number, index) in numbers">
        <span v-if="number != 'c'">
            text: {{ number }}-{{ index }}
        </span>
    </p>
    <button @click="numbers.push('Hello')">Add</button>
</template>