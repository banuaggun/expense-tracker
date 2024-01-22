<template>
  <div>
    <div class="income area">
      <div class="income-content">
        <div class="income-content-header">
          <i class="ph-trend-up ph-bold"></i>
          <span>Income</span>
        </div>
        <div class="income-content-total">
          <span>$ {{income}}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import {defineProps} from 'vue';

const props = defineProps({
  income:{
    type:Number,
    required:true
  }
})
</script>

<style scoped>
.income{
  width:280px;
  margin:0 auto;
  margin:10px auto 20px auto;
  border-bottom:4px solid #0B790B;
}
.income-content-header{
  margin-left:20px;
  display:flex;
  align-items: center;
}
.income-content-header i{
  font-size:32px;
  color:#0B790B;
}
.income-content-header span{
  font-size:18px;
  font-family:'Lora', serif;
  margin-left:8px;
}
.income-content-total{
  margin-bottom:16px;
  margin-top:20px;
  text-align:center;
}
.income-content-total span{
  font-family:'Oxanium', sans-serif;
  font-size:32px;
  font-weight:600;
}
@media only screen and (min-width:620px) and (max-width:820px){
  .income{
    width:340px;
  }
}
@media only screen and (min-width:821px) and (max-width:1025px){
  .income{
    width:280px;
  }
}
@media only screen and (min-width:1026px) and (max-width:1940px){
  .income{
    width:340px;
  }
  .income-content-header i{
    font-size:36px;
  }
  .income-content-header span{
    font-size:16px;
  }
  .incom-content-total span{
    font-size:36px;
  }
}
</style>
