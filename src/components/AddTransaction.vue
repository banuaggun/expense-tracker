<template>
  <div>
    <div class="add">
      <div class="add-header">
        <span>Add New Transaction</span>
      </div>
      <div class="add-form">
        <form id="form" @submit.prevent="onSubmit">
          <div class="add-form-control">
            <label>Income or Expense</label>
            <div class="input-area input-effect">
              
              <input class="effects" type="text" id="text" v-model="text" />
              <span class="focus-border">
                <i></i>
              </span>
            </div>
          </div>
          <div class="add-form-control">
            <label>Amount</label>
            <div class="input-area input-effect">
              
              <input class="effects" type="text" id="amount" v-model="amount" />
              <span class="focus-border">
                <i></i>
              </span>
            </div>              
          </div>
          <div class="add-form-info">
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

.add-form-control label{
  margin-bottom:4px;
  font-weight:500;
  font-family:'Lora', serif;
  font-size:14px;
}

/* input style area */

:focus {
    outline: none;
}
input[type="text"] {
    font: 12px/24px 'Oxanium', sans-serif;
    color: #121212;
    width: 100%;
    box-sizing: border-box;
    letter-spacing: 1px;
}
.input-area {
    position: relative;
}
input[type="text"] {
    font: 12px/24px 'Oxanium', sans-serif;
    color: #121212;
    width: 100%;
    box-sizing: border-box;
    letter-spacing: 1px;
    font-weight:500;
}
.effects {
    border: 1px solid #ccc;
    padding: 7px 14px;
    transition: 0.4s;
    background: transparent;
}
.effects ~ .focus-border:before,
.effects ~ .focus-border:after {
    content: "";
    position: absolute;
    top: 0;
    right: 0;
    width: 0;
    height: 2px;
    background-color: cadetblue;
    transition: 0.2s;
    transition-delay: 0.2s;
}
.effects ~ .focus-border:after {
    top: auto;
    bottom: 0;
    right: auto;
    left: 0;
    transition-delay: 0.6s;
}
.effects ~ .focus-border i:before,
.effects ~ .focus-border i:after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 2px;
    height: 0;
    background-color: cadetblue;
    transition: 0.2s;
}
.effects ~ .focus-border i:after {
    left: auto;
    right: 0;
    top: auto;
    bottom: 0;
    transition-delay: 0.4s;
}
.effects:focus ~ .focus-border:before,
.effects:focus ~ .focus-border:after,
.has-content.effects ~ .focus-border:before,
.has-content.effects ~ .focus-border:after {
    width: 100%;
    transition: 0.2s;
    transition-delay: 0.6s;
}
.effects:focus ~ .focus-border:after,
.has-content.effects ~ .focus-border:after {
    transition-delay: 0.2s;
}
.effects:focus ~ .focus-border i:before,
.effects:focus ~ .focus-border i:after,
.has-content.effects ~ .focus-border i:before,
.has-content.effects ~ .focus-border i:after {
    height: 100%;
    transition: 0.2s;
}
.effects:focus ~ .focus-border i:after,
.has-conten.effects ~ .focus-border i:after {
    transition-delay: 0.4s;
}
.effects ~ label {
    position: absolute;
    left: 14px;
    width: 100%;
    top: 10px;
    color: #aaa;
    transition: 0.3s;
    z-index: -1;
    letter-spacing: 0.5px;
}
.effects:focus ~ label,
.has-content.effects ~ label {
    top: -18px;
    left: 0;
    font-size: 12px;
    color: cadetblue;
    transition: 0.3s;
}

/* input style area */


.add-form-info p{
  font-weight:400;
  font-size:12px;
  font-family:'Oxanium', serif;
  margin:0;
}

.add-form-info p:nth-child(2){
  margin-bottom:20px;
  margin-top:5px;
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