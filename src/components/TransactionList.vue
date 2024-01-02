<template>
<div>
    <div class="transaction">
        <div class="transaction-area">
<div class="transaction-area-header">
            <span>Transaction History</span>
        </div>
         <div class="transaction-area-list">
            <ul id="list" class="list">
                <li v-for="transaction in transactions" :key="transaction.id">
                    <div class="item">
 <span>{{ transaction.text }}</span> 
                    <span>${{ transaction.amount }}</span>
                    <button class="delete-button">X</button>
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

const props = defineProps({
    transactions: {
        type: Array,
        required: true,
    },
});
</script>

<style>
.transaction{
    width:100%;
    position:relative;
}

.transaction-area{
    display:flex;
    justify-content: space-around;
}

.transaction-area-list{
    min-width:100%;
    padding: 10px;
}

</style>
