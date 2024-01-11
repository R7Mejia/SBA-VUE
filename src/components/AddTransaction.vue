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
import { ref } from 'vue';
import {useToast} from 'vue-toastification'

const text = ref('');
const amount = ref('');

const emit = defineEmits(['transactionDeleted']);

const deleteTransaction = (id) => {
  emit('transactionDeleted', id);
};

const toast = useToast();

const onSubmit = () => {
    if (!text.value || !amount.value) {
        toast.error('Es obligatorio llenar ambos campos *');
        return;
    }
    const transactionData = {
        text: text.value,
        amount: parseFloat(amount.value)
    }

emit('transactionSubmitted', transactionData)

    text.value = '';
    amount.value = '';
}
</script>


