<template>
  <div>
    <h4>Tu Saldo es:</h4>
    <div class="calculator">
      <img src="../images/AppBackground.png" alt="Calculator">
      <h1 id="balance" class="balance-overlay">$ {{ total }}</h1>
    </div>
  </div>
</template>

<style scoped>
img {
  position: center;
    width: 100%;
    height: 20vh;
    margin-left: 27px;
    margin-bottom: 0;
}
.calculator {
  position: relative;
  display: inline-block;
}

#balance {
  position: absolute;
  top: 50%;
  left: 55%;
  transform: translate(-50%, -50%);
  font-size: 1.5rem;
  color: rgb(255, 255, 250);
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
  z-index: 1;
}
</style>

<script setup>
const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
});
</script>
