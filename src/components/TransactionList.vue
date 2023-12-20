<template>
    <h4>Transactions History</h4>
    <ul id="list" class="list">
        <li v-for="transaction in transactions" :key="transaction.id">
            {{ transaction.text }} <span>${{ transaction.amount }}</span>
            <button class="delete-button">X</button>
        </li>
    </ul>
</template>

<script>
export default {
    data() {
        return {
            transactions: [
                { id: 1, text: "Grocery", amount: -250.85 },
                { id: 2, text: "Salary", amount: 4000.0 },
                { id: 3, text: "Book", amount: -400.5 },
                { id: 4, text: "Fund Investment", amount: 400.2 },
            ],
        };
    },
};
</script>

<style></style>
