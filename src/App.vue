<script setup>
import { reactive } from 'vue';

const estado = reactive({
  operacao: 'soma',
  num:[
    {
      num1: 0,
      num2: 0,
    }
  ]
})

const addNum = () => {
  const newNum = {
    num1: estado.tempnum1,
    num2: estado.tempnum2,
  }
  estado.num.push(newNum);
}

const getSoma = () => {
    return parseFloat(estado.num.num1) + parseFloat(estado.num.num2)
  }

  const getSubtracao = () => {
    return parseFloat(estado.num.num1) - parseFloat(estado.num.num2)
  }

  const getDivisao = () => {
    return parseFloat(estado.num.num1) / parseFloat(estado.num.num2)
  }

  const getMultiplicadao = () => {
    return parseFloat(estado.num.num1) * parseFloat(estado.num.num2)
  }

const getOperacao = () => {
    const { operacao } = estado;

    switch (operacao) {
      case 'soma':
        return getSoma();
      case 'subtracao':
        return getSubtracao();
      case 'divisao':
        return getDivisao();
      case 'multiplicao':
        return getMultiplicadao();
    }
  }

  const operacaoSymbol = () => {
    const { operacao } = estado;

    switch (operacao) {
      case 'soma':
        return "+";
      case 'subtracao':
        return "-";
      case 'divisao':
        return "/";
      case 'multiplicao':
        return "*";
    }
  }

</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-primary-subtle rounded-3">
      <h1>Calculadora Aritimética</h1>
    </header>

    <form>
      <div class="row">
        <div class="col">
          <input @keyup="evento => estado.num.num1 = evento.target.value" type="number" class="form-control" placeholder="0" > 
        </div>

        <div class="col">
          <select @change="evento => estado.operacao = evento.target.value" class="form-control">
            <option value="soma">Soma</option>
            <option value="subtracao">Subtração</option>
            <option value="divisao">Divisão</option>
            <option value="multiplicao">Multiplição</option>
          </select>
        </div>

        <div class="col">
          <input @keyup="evento => estado.num.num2 = evento.target.value" type="number" class="form-control" placeholder="0" > 
        </div>
      </div>
    </form>

  <h3>{{estado.num.num1}} {{ operacaoSymbol() }} {{estado.num.num2}} = {{ getOperacao() }}</h3>

  </div>
</template>

<style scoped>
</style>
