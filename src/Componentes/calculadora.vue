<script setup>
import { reactive } from 'vue';

 const estado = reactive({
    primeiroNumero: '',
    segundoNumero: '',
    operações: {
        somar: (a, b) => a + b,
        subtração: (a, b) => a - b,
        multiplicação: (a, b) => a * b,
        divisão: (a, b) => (b !== 0 ? a / b : 'Divisão por zero'),
    },
    resultado: 0,
});

const calcularResultado = () => {
    const { primeiroNumero, segundoNumero, operaçãoMatematica } = estado;
    estado.resultado = estado.operações[operaçãoMatematica](parseFloat(primeiroNumero), parseFloat(segundoNumero));
};
</script>
<template>
<div class="container">
    <H1>Calculadora</H1><br>

  <h2>Digite um número</h2>
  <input type="number" v-model="estado.primeiroNumero" @input="calcularResultado"><br>
  <h2>Digite outro número</h2>
  <input type="number" v-model="estado.segundoNumero" @input="calcularResultado"><br>
  <br>

  <h2>Escolha a operação matematica</h2>
  <select v-model="estado.operaçãoMatematica" @change="calcularResultado">
    <option value="somar">Somar</option>
    <option value="subtração">Subtrair</option>
    <option value="multiplicação">Multiplicar</option>
    <option value="divisão">Dividir</option>
    </select>
    <h2>Resultado</h2><br>
    <h3>{{ estado.resultado }}</h3>

  </div>
</template>

<style scoped>
  .container{
    
    margin-top: 5%;
    padding: 10px;
    border-radius: 10%;
    text-align: center;
    background-color: red;
  }
</style>