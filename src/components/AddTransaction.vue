<template>
  <div>
    <div class="add">
      <div class="add-header">
        <span>Add New Transaction</span>
      </div>
      <div class="add-form">
        <form id="form">
          <div class="add-form-control">
            <label for="text">Text</label>
            <input type="text" id="text" placeholder="Enter Text..." />
          </div>
          <div class="add-form-control">
            <label for="amount">
              Amount
              (negative - expense, positive - income)
            </label>
            <input type="number" id="amount" placeholder="Enter Amount..." />
          </div>
          <div class="add-form-button">
            <button>Add Transaction</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  
}
</script>
