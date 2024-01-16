<template>
    <div class="content">
        <Header />
        <div class="container">

            <div class="container-top">
                <div class="container-top-col-1">
                    <Balance :total="+total" />
                </div>
                <div class="container-top-col-2">
                    <Income :income="+income" />
                    
                </div>
                <div class="container-top-col-3">
                    <Expenses :expenses="+expenses" />
                </div>
            </div>

            <div class="container-bottom">
                <div class="container-bottom-col-1">
                    <AddTransaction @transactionSubmitted="handleTransactionSubmitted" />
                </div>
                <div class="container-bottom-col-2">
                    <TransactionList @transactionDeleted="handleTransactionDeleted" :transactions="transactions" />
                </div>
            </div>
            
        </div>      
    </div>
</template>

<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import Income from './components/Income.vue';
import Expenses from './components/Expenses.vue';
import AddTransaction from "./components/AddTransaction.vue";
import TransactionList from "./components/TransactionList.vue";

import { ref, computed, onMounted } from "vue";
import { useToast } from "vue-toastification";

const toast = useToast();

const transactions = ref([]);

onMounted(() => {
    const savedTransactions = JSON.parse(localStorage.getItem('transactions'));
    if(savedTransactions){
        transactions.value = savedTransactions
    }
})
/*
const transactions = ref([
    { id: 1, text: "Grocery", amount: -250.85 },
    { id: 2, text: "Salary", amount: 4000.0 },
    { id: 3, text: "Book", amount: -400.5 },
    { id: 4, text: "Fund Investment", amount: 400.2 },
]);
*/

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
    saveTransactionsToLocalStorage();
    toast.success('Transaction added');
};

// generateUniqueId
const generateUniqueId = () => {
    return Math.floor(Math.random() * 1000000);
}

// delete transaction
const handleTransactionDeleted = (id) => {
    transactions.value = transactions.value.filter((transaction) => transaction.id !== id);
    saveTransactionsToLocalStorage();
    toast.success('Transaction Deleted');
}

// save to localStorage
const saveTransactionsToLocalStorage = () => {
    localStorage.setItem('transactions', JSON.stringify(transactions.value));
}
</script>

<style scoped>
.container{
    max-width:1100px;
    margin:20px auto;
}
.container-top{
    display:grid;
    grid-template-columns: repeat(3, 340px);
    justify-content:space-between;
}
.container-bottom{
    display:grid;
    grid-template-columns: 22rem auto;
    grid-gap:20px;
}
</style>