<template>
  <div>
    <div class="add">
      <div class="add-header">
        <span>Add New Transaction</span>
      </div>
      <div class="add-form">
        <form id="form" @submit.prevent="onSubmit">
          <div class="add-form-control">
            <label for="text">Text</label>
            <input type="text" id="text" v-model="text" placeholder="Enter Text..." />
          </div>
          <div class="add-form-control">
            <label for="amount">
              Amount
              (negative - expense, positive - income)
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
  width:100%;
  min-width:max-content;
  display:flex;
  flex-direction: column;
}

.add-header{
  font-weight:600;

}
.add-form{
  margin:20px auto;
}

.add-form-control{
  display: flex;
  flex-direction: column;
  margin:16px auto;
}

.add-form-control label{
  margin-bottom:8px;
  text-transform: uppercase;
  font-weight:600;

}

.add-form-control input{
  width:100%;
  height:44px;
  border:none;
  outline:none;
  border-radius:4px;
  border-bottom:4px solid cadetblue;
  background-color: whitesmoke;
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