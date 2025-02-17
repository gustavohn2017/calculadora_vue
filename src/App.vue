<script setup>
import { ref, watch } from 'vue';
// ref e watch para criar variáveis reativas e observar mudanças
// watch para observar mudanças nas variáveis reativas e chamar a função calcular
const num1 = ref(0);
const num2 = ref(0);
const operacao = ref('+');
const result = ref(0);

watch([num1, num2, operacao], () => {
  calcular();
});
 // parse float para converter o valor para número decimal
 // switch case para verificar a operação selecionada
 // e realizar a operação matemática
 // 
function calcular() {
  const n1 = parseFloat(num1.value);
  const n2 = parseFloat(num2.value);

  switch (operacao.value) {
    case '+':
      result.value = n1 + n2;
      break;
    case '-':
      result.value = n1 - n2;
      break;
    case '*':
      result.value = n1 * n2;
      break;
    case '/':
      result.value = n1 / n2;
      break;
  }
}
</script>

<template>
  <section class="container">
    <div class="aritmetica">
      <h1 class="titulo">Calculadora Aritmética</h1>
      <p class="text">Calculadora aritmética baseada em inputs</p>
    </div>
    <div class="inputs">
      <input type="number" v-model="num1" placeholder="Digite o primeiro número" />
      <select v-model="operacao">
        <option value="+">Soma</option>
        <option value="-">Subtração</option>
        <option value="*">Multiplicação</option>
        <option value="/">Divisão</option>
      </select>
      <input type="number" v-model="num2" placeholder="Digite o segundo número" />
    </div>
    <div class="resultado">
      <h2>Resultado: {{ result }}</h2>
    </div>
  </section>

  <section class="container">
    <h1 class="titulo">Calculadora</h1>
    
    <div class="calculadora">
      <div class="display">{{ current || '0' }}</div>
      <div class="btn" @click="clear">C</div>
      <div class="btn" @click="inputOperator('%')">%</div>
      <div class="btn" @click="inputOperator('/')">/</div>
      <div class="btn" @click="calculateResult">=</div>
      <div class="btn" @click="inputDigit('7')">7</div>
      <div class="btn" @click="inputDigit('8')">8</div>
      <div class="btn" @click="inputDigit('9')">9</div>
      <div class="btn" @click="inputOperator('*')">*</div>
      <div class="btn" @click="inputDigit('4')">4</div>
      <div class="btn" @click="inputDigit('5')">5</div>
      <div class="btn" @click="inputDigit('6')">6</div>
      <div class="btn" @click="inputOperator('-')">-</div>
      <div class="btn" @click="inputDigit('1')">1</div>
      <div class="btn" @click="inputDigit('2')">2</div>
      <div class="btn" @click="inputDigit('3')">3</div>
      <div class="btn" @click="inputOperator('+')">+</div>
      <div class="btn" @click="inputDigit('0')">0</div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      current: '',
    };
  },
  methods: {
    calcular() {
      this.result = eval(this.current);
    },
    clear() {
      this.current = '';
    },
    inputDigit(digit) {
      this.current += digit;
    },
    inputOperator(operator) {
      this.current += operator;
    },
    calculateResult() {
      this.current = eval(this.current);
    },
  },
}
</script>

<style scoped>
.container {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f5f5f5;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.aritmetica {
  text-align: center;
  margin-bottom: 20px;
}

.titulo {
  font-size: 2rem;
  color: #333;
}

.text {
  font-size: 1.2rem;
  color: #666;
}

.inputs {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-bottom: 20px;
}

.inputs input,
.inputs select {
  padding: 10px;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.resultado {
  text-align: center;
}

.resultado h2 {
  font-size: 1.5rem;
  color: #333;
}

.calculadora {
  margin: 0 auto;
  width: 300px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  font-size: 1.5rem;
  gap: 10px;
  padding: 10px;
  background-color: #f0f0f0;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.display {
  grid-column: 1 / -1;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  background-color: #000;
  color: #fff;
  font-size: 2rem;
  text-align: right;
  padding: 10px;
  border-radius: 10px;
}

.btn {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #ddd;
  color: #000;
  border-radius: 5px;
  cursor: pointer;
  user-select: none;
  transition: background-color 0.3s ease;
}

.btn:active {
  background-color: #ccc;
}

.btn:nth-child(4n+1) {
  background-color: #ff7f50;
  color: #fff;
}

.btn:nth-child(4n+1):active {
  background-color: #e06b40;
}
</style>
