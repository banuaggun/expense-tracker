<template>
<div>
    <div class="transaction">
        <div class="transaction-header">
            <span>Transaction History</span>
        </div>
        <div class="transaction-area">
            <div class="transaction-area-list list-1">
                <div class="transaction-area-list-header">
                    <span>Incomes</span>
                </div>
                <div class="transaction-area-list-item">
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
                
            </div>
            <div class="transaction-area-list list-2">
                <div class="transaction-area-list-header">
                    <span>Expenses</span>
                </div>
                <div class="transaction-area-list-item">
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
    margin:0 20px 20px 20px;
    border:1px solid green;
}
.transaction-header{
    font-size: 18px;
    font-weight:600;
    font-family:'Lora', serif;
}
.transaction-area-list-header span{
    font-size:16px;
    font-weight:500;
    font-family:'Lora', serif;
    border-bottom:1px solid #121212;
    padding-bottom:2px;
}
.list-1{
    margin-top:20px;
}
.transaction-area-list-item ul{
    border:1px solid violet;
    width:100%;
    margin:10px 0 20px 0;
    padding:0;
}
.transaction-area-list-item ul li{
    margin-left:10px;
    margin-bottom:10px;
}
.transaction-area-list-item .item{
    display:flex;
    justify-content: space-between;
    align-content:flex-start;
    align-items:center;
    text-transform: capitalize;
    font-size: 14px;
}
.transaction-area-list-item .item span,
.transaction-area-list-item .item button{
    width:33.33%;
}
.transaction-area-list-item .item span:nth-child(1){
    font-weight:500;
}
.transaction-area-list-item .item span:nth-child(2){
    font-weight:700;
    letter-spacing:0.4px;
}
.transaction-area-list-item .item button{
    width:36px;
    height:36px;
    border:1px solid #ccc;
    outline:none;
    background-color:floralwhite;
    border-radius:4px;
    color:rgba(18, 18, 18, 0.8);
    font-size:18px;
    font-weight: 700;
}
.transaction-area-list-item .item button:hover,
.transaction-area-list-item .item button.active{
    background-color:red;
    color:floralwhite;
    border:none;
}
@media only screen and (min-width:450px) and (max-width:700px){
  .transaction{
    margin:0 60px 20px 60px;
  }
}
@media only screen and (min-width:701px) and (max-width:820px){
  .transaction{
    width: 60%;
    margin:0 auto 20px auto;
  }
  .transaction-header{
    font-size:22px;
  }
  .transaction-area-list-header span{
    font-size:20px;
  }
  .transaction-area-list-item .item{
    font-size:16px;
  }
}
@media only screen and (min-width:821px) and (max-width:1960px){
  .transaction{
    margin:0 20px 20px auto;
  }
  .transaction-header{
    font-size:26px;
  }
  .transaction-area-list-header span{
    font-size:16px;
  }
  .transaction-area-list-item .item{
    font-size:16px;
  }
  .transaction-area {
      width:100%;
      display: flex;
      align-items:flex-start;
      justify-content: space-between;
  }
  .transaction-area-list{
      width:45%;
      border:1px solid green;
  }
  .list-1,
  .list-2{
      margin-top:20px;
  }
}

</style>
