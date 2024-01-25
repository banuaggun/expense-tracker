<template>
  <div>
    <div class="add">
      <div class="add-header">
        <span>Add New Transaction</span>
      </div>
      <div class="add-form">
        <form id="form" @submit.prevent="onSubmit">
          <div class="add-form-control">
            <label for="text">
              <span>
                Income or Expense Name
              </span>
            </label>
            <input type="text" id="text" v-model="text" placeholder="Enter Text..." />
          </div>
          <div class="add-form-control">
            <label for="amount">
              <span>
                Amount
              </span>
              <p>
                <i>
                  If it is an expense, write it as a negative value (-)
                </i>
              </p>
              <p>
                <i> 
                  if it is a positive value, write it directly.
                </i>
              </p>
            </label>
            
            <input type="text" id="amount" v-model="amount" placeholder="Enter Amount..." />
          </div>
          <div class="add-form-button">
            <button>Add Transaction</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>
<script setup>
import {ref} from 'vue';
import {useToast} from 'vue-toastification'

const text = ref('');
const amount = ref('');

const emit = defineEmits(['transactionSubmitted'])

const toast = useToast();

const onSubmit = () => {
  if(!text.value || !amount.value){
    toast.warning('Both field must be filled!');
    return;
  }
  const transactionData = {
    text:text.value,
    amount:parseFloat(amount.value)
  };
  emit('transactionSubmitted', transactionData);
  text.value='';
  amount.value='';
}
</script>


<style scoped>
.add{
  display:flex;
  flex-direction: column;
  margin:0 20px 20px 20px;
  border:1px solid blue;
}

.add-header{
  font-weight:600;
  font-family: 'Lora', sans-serif;
  color:#121212;
}
.add-form-control{
  display: flex;
  flex-direction: column;
  margin:16px auto;
}

.add-form-control label span{
  text-transform: uppercase;
  font-weight:500;
  font-size:14px;
  font-family: 'Lora', sans-serif;
}

.add-form-control label p{
  font-weight:400;
  font-size:12px;
  font-family:'Oxanium', serif;
}

.add-form-control input{
  height:44px;
  border:none;
  outline:none;
  border-radius:4px;
  border-bottom:4px solid cadetblue;
  background-color: snow;
}

.add-form-button{
  display:flex;
  justify-content: center;

}
.add-form-button button{
  border:none;
  outline:none;
  padding:16px 0px;
  width:80%;
  border-radius:4px;
  font-size:1.2rem;
  font-weight:600;
  text-transform: uppercase;
  background-color: lightseagreen;
}
</style>