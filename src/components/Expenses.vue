<template>
  <div>
    <div class="area">
      <div class="area-content">
        <div class="area-content-expenses">
          <div class="area-content-expenses-header">
            <span>Expenses</span>
          </div>
          <div class="area-content-expenses-total">
            <span>$ {{Math.abs(expenses)}}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import {defineProps} from 'vue';

const props = defineProps({
  expenses:{
    type:Number,
    required:true
  }
})
</script>

<style scoped>
.area{
  border:1px solid purple;
}
</style>