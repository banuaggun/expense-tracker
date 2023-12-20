<template>
  <Header />
  <div class="container">
    <Balance />
    <TransactionList />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Balance from './components/Balance.vue'
import TransactionList from './components/TransactionList.vue'
export default{
  components:{
    Header,
    Balance,
    TransactionList
  }
}
</script>

