<template>
  <div>
    <div class="balance">
      <div class="balance-header">
        <span>Your Balance</span>
      </div>
      <div class="balance-total">
        <span id="balance">${{total}}</span>
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