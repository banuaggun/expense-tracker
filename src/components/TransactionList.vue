<template>
<div>
    <div class="transaction">
        <div class="transaction-area">
<div class="transaction-area-header">
            <span>Transaction History</span>
        </div>
         <div class="transaction-area-list">
            <ul id="list-income" class="list-income">
                <li v-for="transaction in transactions" v-show="transaction.amount > 0" :key="transaction.id">
                  
                    <div class="item">
 <span>{{ transaction.text }}</span> 
                    <span>${{ transaction.amount }}</span>
                    <button @click="deleteTransaction(transaction.id)" class="delete-button">X</button>
                    </div>
                   
                </li>
            </ul>
        </div>
        <div class="transaction-area-list">
            <ul id="list-expenses" class="list-expenses">
                <li v-for="transaction in transactions" v-show="transaction.amount < 0" :key="transaction.id">
                  
                    <div class="item">
 <span>{{ transaction.text }}</span> 
                    <span>${{ Math.abs(transaction.amount) }}</span>
                    <button @click="deleteTransaction(transaction.id)" class="delete-button">X</button>
                    </div>
                   
                </li>
            </ul>
        </div>
        </div>
        
       
    </div>
</div>
    
</template>

<script setup>

import { defineProps } from "vue";

const emit = defineEmits(['transactionDeleted']);

const props = defineProps({
    transactions: {
        type: Array,
        required: true,
    },
});

const deleteTransaction = (id) => {
    emit('transactionDeleted', id);
}
</script>

<style>
.transaction{
    border:1px solid green;
}
</style>
