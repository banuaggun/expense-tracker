<template>
    <div class="content">
        <Header />
        <div class="container">

            <div class="container-top">
                <div class="container-top-col-1 col">
                    <Balance :total="+total" />
                </div>
                <div class="container-top-col-2 col">
                    <Income :income="+income" />
                    
                </div>
                <div class="container-top-col-3 col">
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
.content{
    width:100%;
    max-width:100%;
    min-width:100%;
    overflow-x:hidden;
}
.container{
    margin:80px auto 20px auto;
    position:relative;
}
.container-bottom{
    display: flex;
    flex-direction:column;
    margin-top:40px;
}
@media only screen and (min-width:700px) and (max-width:830px){
    .container{
        margin:0px auto 20px auto;
    }
}
@media only screen and (min-width:832px) and (max-width:1026px){
    .container{
        margin:0 auto 30px auto;
    }
    .container-top{
        margin:30px auto 30px auto;
    }
    .container-bottom{
        width:60%;
        margin:0 auto;
    }
}
@media only screen and (min-width:1027px) and (max-width:1940px){
    .container{
        max-width:1100px;
        margin:20px auto;
    }
    .container-top{
        display:flex;
        align-items:center;
        justify-content: space-evenly;
    }
    .container-bottom{
        margin-top:20px;
        display:grid;
        flex-direction:row;
        grid-template-columns:26rem auto;
        grid-gap:20px;
    }
}



/*
.content{
    width:100%;
}
.container{
    max-width:1100px;
    width:100%;
    margin:20px auto;
}
.container-top{
    display:grid;
    grid-template-columns: repeat(3, 340px);
    justify-content:space-between;
    margin-bottom:20px;
}
.container-bottom{
    display:grid;
    grid-template-columns: 22rem auto;
    grid-gap:20px;
}
@media screen and (max-width:400px){
    .container,
    .content{
        width:100%;
    }
    .container-top{
        display:grid;
        flex-direction:column;
        justify-content: center;
        grid-template-columns:repeat(auto-fit, 300px);
    }
    .col{
        margin:0 auto;
    }
    .container-bottom{
        display:grid;
        flex-direction: column;
        grid-template-columns: repeat(auto-fit, 300px);
    }
}
*/
</style>