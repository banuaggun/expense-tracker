<template>
    <h4>Transactions History</h4>
    <ul id="list" class="list">
        <li v-for="transaction in transactions" :key="transaction.id">
            {{ transaction.text }} <span>${{ transaction.amount }}</span>
            <button class="delete-button">X</button>
        </li>
    </ul>
</template>

<script setup>

import { defineProps } from "vue";

const props = defineProps({
    transactions: {
        type: Array,
        required: true,
    },
});
</script>

<style></style>
