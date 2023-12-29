<template>
    <div>
        <h3>Income</h3>
        <p>${{ income }}</p>
        <h3>Expenses</h3>
        <p>${{ expenses }}</p>
    </div>
</template>
<script setup>
import { defineProps } from "vue";

const props = defineProps({
    income: {
        type: Number,
        required: true,
    },
    expenses: {
        type: Number,
        required: true,
    },
});
</script>
