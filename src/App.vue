<script setup>
  import {reactive} from "vue"

  const estado = reactive ({
    num1: 0,
    num2: 0,
    resultado: 0,
    operador: 'soma', 
  })

  function getNumber1(evento) {
  estado.num1 = evento.target.value;
  if (estado.num1 == '')  {
    estado.num1 = 0;
  }
  estado.num1 = parseFloat(estado.num1)
  getOperacao();
}

function getNumber2(evento) {
  estado.num2 = evento.target.value;
  if (estado.num2 == '')  {
    estado.num2 = 0;
  }
  estado.num2 = parseFloat(estado.num2)
  getOperacao();
}

function getOperador(evento) {
  estado.operador = evento.target.value;
  getOperacao();
}

  const soma = () => {
    return estado.resultado = (estado.num1 + estado.num2);
  }

  const subtrai = () => {
    return estado.resultado = (estado.num1 - estado.num2);
  }

  const dividi = () => {
    return estado.resultado = (estado.num1 / estado.num2);
  }

  const multiplica = () => {
    return estado.resultado = (estado.num1 * estado.num2);
  }

  const getOperacao = () => {
    const {filtro} = estado;

    switch (filtro) {
      case 'soma':
        return soma();
      case 'subtrai':
        return subtrai();
      case 'dividi':
        return dividi();
      case 'multiplica':
        return multiplica();
    }
  }
</script>

<template>
  <div class="container text-center">
    <h1 class="p-3">Calculadora aritmética</h1>

    <input class="me-3" type="number" id="num1" placeholder="Primeiro número" @keyup="getNumber1()">
    <input class="me-3" type="number" id="num2" placeholder="Segundo número" @keyup="getNumber2()">
    <label class="me-3" for="operacao">Escolha a operação</label>
    <select id="operacao" @change="getOperador()">
      <option selected value="soma">Soma</option>
      <option value="subtrai">Subtração</option>
      <option value="multiplica">Multiplicação</option>
      <option value="dividi">Divisão</option>
    </select>
    <br>
    <br>
    <span>O resultado da operação é: {{ estado.resultado }}</span>
  </div>
</template>

<style scoped>
  span{
    font-size: 18px;
  }
</style>
