<template>
    <Header />
    <div class="container">
        <Balance :total="total" />
        <IncomeExpenses :income="income" :expenses="expenses" />
        <TransactionList :transactions="transactions" />
    </div>
</template>

<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpenses from "./components/IncomeExpenses.vue";
import TransactionList from "./components/TransactionList.vue";

import { ref, computed } from "vue";

const transactions = ref([
    { id: 1, text: "Grocery", amount: -250.85 },
    { id: 2, text: "Salary", amount: 4000.0 },
    { id: 3, text: "Book", amount: -400.5 },
    { id: 4, text: "Fund Investment", amount: 400.2 },
]);

// total
const total = computed(() => {
    return transactions.value.reduce((acc, transaction) => {
        return acc + transaction.amount;
    }, 0);
});

// income
const income = computed(() => {
    return transactions.value.filter((transaction) => transaction.amount > 0).reduce((acc, transaction) => {
        return acc + transaction.amount;
    }, 0).toFixed(2);
});

// expenses
const expenses = computed(() => {
    return transactions.value.filter((transaction) => transaction.amount < 0).reduce((acc, transaction) => {
        return acc + transaction.amount;
    }, 0).toFixed(2);
});
</script>
