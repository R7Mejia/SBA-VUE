<template>
    <h3>Añadir nueva transacción</h3>
  <form id="form" @submit.prevent="onSubmit">
    <div class="form-control">
      <label for="text">Texto *</label>
      <input 
      type="text" 
      id="text" 
      v-model="text"
      placeholder="Ingresa texto..."  />
    </div>
    <div class="form-control">
      <label for="amount">Cantidad *<br />
        (negativo - gasto, positivo - ingreso)</label>
      <input
        type="text"
        id="amount"
        v-model="amount"
        placeholder="Ingresa la Cantidad $..."/>
    </div>
    <button class="btn">Añadir Transacción</button>
  </form>
</template>

<script setup>
import { useToast } from 'vue-toastification';
import { ref } from 'vue';

const text = ref('');
const amount = ref('');

// Get toast interface
const toast = useToast();

const emit = defineEmits(['transactionSubmitted']);

const onSubmit = () => {
  if (!text.value || !amount.value) {
    // Display a toast error message if either field is empty
    toast.error('Es obligatorio llenar ambos *.');
    return;
  }

  const transactionData = {
    text: text.value,
    amount: parseFloat(amount.value),
  };

  emit('transactionSubmitted', transactionData);

  // Clear form fields
  text.value = '';
  amount.value = '';
};
</script>