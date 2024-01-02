<template>
  <div>
    <div class="balance">
      <div class="balance-content">
        <div class="balance-content-header">
        <span>Your Balance</span>
      </div>
      <div class="balance-content-total">
        <span id="balance">${{total}}</span>
      </div>
      </div>    
    </div>
  </div>
</template>

<script setup>
import {defineProps} from 'vue'

const props = defineProps({
  total:{
    type:Number,
    required:true,
  }
})
</script>

