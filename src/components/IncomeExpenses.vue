<template>
    <div>
        <div class="area">
            <div class="area-content">
                <div class="area-content-income">
                <div class="area-content-income-header">
                    <span>Income</span>
                </div>
                <div class="area-content-income-total">
                    <span>$ {{income}}</span>
                </div>
            </div>
            <div class="area-content-expenses">
                <div class="area-content-expenses-header">
                    <span>Expenses</span>
                </div>
                <div class="area-content-expenses-total">
                    <span>$ {{expenses}}</span>
                </div>
            </div>
            </div>
        </div>
    </div>
</template>
<script setup>
import { defineProps } from "vue";

const props = defineProps({
    income: {
        type: Number,
        required: true,
    },
    expenses: {
        type: Number,
        required: true,
    },
});
</script>

