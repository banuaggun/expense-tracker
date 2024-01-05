<template>
    <div class="content">
        <Header />
        <div class="container">

            <div class="container-left">
                <div class="container-left-row-1">
                    <Balance :total="+total" />
                </div>
                <div class="container-left-row-2">
                    <IncomeExpenses :income="+income" :expenses="+expenses" />
                </div>
            </div>

            <div class="container-right">
                <div class="container-right-row">
                    <AddTransaction @transactionSubmitted="handleTransactionSubmitted" />
                </div>
                <div class="container-right-row">
                    <TransactionList @transactionDeleted="handleTransactionDeleted" :transactions="transactions" />
                </div>
            </div>
            
        </div>      
    </div>
</template>

<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpenses from "./components/IncomeExpenses.vue";
import AddTransaction from "./components/AddTransaction.vue";
import TransactionList from "./components/TransactionList.vue";

import { ref, computed } from "vue";
import { useToast } from "vue-toastification";

const toast = useToast();

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

// add transaction
const handleTransactionSubmitted = (transactionData) => {
    transactions.value.push({
        id:generateUniqueId(),
        text:transactionData.text,
        amount:transactionData.amount
    });
    toast.success('Transaction added');
};

// generateUniqueId
const generateUniqueId = () => {
    return Math.floor(Math.random() * 1000000);
}

// delete transaction
const handleTransactionDeleted = (id) => {
    transactions.value = transactions.value.filter((transaction) => transaction.id !== id);
    toast.success('Transaction Deleted');
}
</script>
