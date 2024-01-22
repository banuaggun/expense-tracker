<template>
  <div>
    <div class="balance area">
      <div class="balance-content">
        <div class="balance-content-header">
          <i class="ph-bold ph-wallet"></i>
        <span>Balance</span>
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

<style scoped>
.balance{
  width:280px;
  margin:0 auto;
  margin:10px auto 20px auto;
  border-bottom:4px solid #315D70;
}
.balance-content-header{
  margin-left:20px;
  display:flex;
  align-items: center;
}
.balance-content-header i{
  font-size:28px;
  color:#315D70;
}
.balance-content-header span{
  font-size:14px;
  font-family:'Lora', serif;
  margin-left:8px;
}
.balance-content-total{
  margin-bottom:16px;
  margin-top:20px;
  text-align:center;
}
.balance-content-total span{
  font-family:'Oxanium', sans-serif;
  font-size:32px;
  font-weight:600;
}
@media only screen and (min-width:620px) and (max-width:820px){
  .balance{
    width:340px;
  }
}
@media only screen and (min-width:821px) and (max-width:1025px){
  .balance{
    width:280px;
  }
}
@media only screen and (min-width:1026px) and (max-width:1940px){
  .balance{
    width:340px;
  }
  .balance-content-header i{
    font-size:36px;
  }
  .balance-content-header span{
    font-size:16px;
  }
  .balance-content-total span{
    font-size:36px;
  }
}
</style>
