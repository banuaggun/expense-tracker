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

const text = ref('');
const amount = ref('');

const onSubmit = () => {

}
</script>
