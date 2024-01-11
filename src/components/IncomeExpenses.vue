<template>
    <div class="inc-exp-container">
        <div>
            <h4>Depósito</h4>
            <p id="money-plus" class="money plus">+$  {{income}} </p>
            <h4>Gasto</h4>
            <p id="money-minus" class="money minus">-${{expenses}}</p>
        </div>
    </div>
</template>

<script setup>
const props = defineProps({
    income: {
        type: Number,
        required: true,
    },
     expenses: {
        type: Number,
        required: true,
    }
})

</script>