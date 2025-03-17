<script setup>
import { ref, computed } from 'vue';
// Definindo os estados reativos
const num1 = ref(0);
const num2 = ref(0);
const operation = ref('+');

// Computed para calcular o resultado automaticamente
const result = computed(() => {
  const a = parseFloat(num1.value);
  const b = parseFloat(num2.value);
  switch (operation.value) {
    case '+': return a + b;
    case '-': return a - b;
    case '*': return a * b;
    case '/': return b !== 0 ? a / b : 'Erro';
    default: return 0;
  }
});
</script>

<template>
  <div class="calculator">
    <input type="number" v-model="num1" placeholder="Número 1" />

    <select v-model="operation">
      <option value="+">+</option>
      <option value="-">-</option>
      <option value="*">*</option>
      <option value="/">/</option>
    </select>

    <input type="number" v-model="num2" placeholder="Número 2" />

    <p>Resultado: {{ result }}</p>
  </div>

</template>

<style scoped>
.calculator {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  padding: 20px;
  max-width: 300px;
  margin: auto;
  background: #f5f5f5;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

input,
select {
  padding: 8px;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 5px;
}
</style>
