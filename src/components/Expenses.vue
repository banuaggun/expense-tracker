<template>
  <div>
    <div class="expenses area">
      <div class="expenses-content">
          <div class="expenses-content-header">
            <i class="ph-trend-down ph-bold"></i>
            <span>Expenses</span>
          </div>
          <div class="expenses-content-total">
            <span>$ {{Math.abs(expenses)}}</span>
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
.expenses{
  width:280px;
  margin:0 auto;
  margin:10px auto 20px auto;
  border-bottom:4px solid #D30404;
}
.expenses-content-header{
  margin-left:20px;
  display:flex;
  align-items: center;
}
.expenses-content-header i{
  font-size:28px;
  color:#D30404;
}
.expenses-content-header span{
  font-size:14px;
  font-family:'Lora', serif;
  margin-left:8px;
}
.expenses-content-total{
  margin-bottom:16px;
  margin-top:20px;
  text-align:center;
}
.expenses-content-total span{
  font-family:'Oxanium', sans-serif;
  font-size:32px;
  font-weight:600;
}
@media only screen and (min-width:620px) and (max-width:820px){
  .expenses{
    width:340px;
  }
}
@media only screen and (min-width:821px) and (max-width:1025px){
  .expenses{
    width:280px;
  }
}
@media only screen and (min-width:1026px) and (max-width:1940px){
  .expenses{
    width:340px;
  }
  .expenses-content-header i{
    font-size:36px;
  }
  .expenses-content-header span{
    font-size:16px;
  }
  .expenses-content-total span{
    font-size:36px;
  }
}
</style>