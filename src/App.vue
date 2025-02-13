<script setup>

</script>

<template>
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
</template>


<script>
export default {
  data() {
    return {
      current: '',
    };
  },
  methods: {
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
