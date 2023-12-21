<template>
  <Header />
  <div class="container">
    <Balance />
    <TransactionList :transactions="transactions" />
  </div>
</template>

<script setup>
import Header from './components/Header.vue'
import Balance from './components/Balance.vue'
import TransactionList from './components/TransactionList.vue'

import {ref} from 'vue'

const transactions = ref([
  { id: 1, text: "Grocery", amount: -250.85 },
  { id: 2, text: "Salary", amount: 4000.0 },
  { id: 3, text: "Book", amount: -400.5 },
  { id: 4, text: "Fund Investment", amount: 400.2 },
]);
</script>

