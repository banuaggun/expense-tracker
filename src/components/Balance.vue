<template>
  <span>Your Balance</span>
  <br/><br/>
  <span id="balance">${{total}}</span>
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