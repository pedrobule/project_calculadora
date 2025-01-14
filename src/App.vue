<script setup>
import { ref, computed } from 'vue';

const num1 = ref(0); 
const num2 = ref(0); 
const operation = ref('+'); 

const result = computed(() => {
  switch (operation.value) {
    case '+':
      return num1.value + num2.value;
    case '-':
      return num1.value - num2.value;
    case '*':
      return num1.value * num2.value;
    case '/':
      return num2.value !== 0 ? num1.value / num2.value : 'Erro: Divisão por zero';
    default:
      return 0;
  }
});
</script>

<template>
  <div id="app">
    <div class="calculadora">
      <h1>Calculadora</h1>

      <div class="input-group">
        <input type="number" v-model.number="num1" placeholder="Número 1" />
        <input type="number" v-model.number="num2" placeholder="Número 2" />
      </div>

      <div class="operacao">
        <select v-model="operation">
          <option value="+">Soma</option>
          <option value="-">Subtração</option>
          <option value="*">Multiplicação</option>
          <option value="/">Divisão</option>
        </select>
      </div>

      <div class="resultado">
        <p>Resultado: {{ result }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.calculadora {
  display: inline-block;
  padding: 20px;
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.input-group {
  margin-bottom: 20px;
}

input {
  width: 100px;
  padding: 8px;
  margin-right: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 1.2rem;
}

select {
  padding: 8px;
  font-size: 1.2rem;
  border-radius: 5px;
  border: 1px solid #ccc;
}

.resultado {
  font-size: 1.5rem;
  font-weight: bold;
  margin-top: 20px;
}
</style>

