<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue'
import Formulario from './components/Formulario.vue'

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
    <Cabecalho/>

    <Formulario :number1="evento => estado.num.num1 = evento.target.value" :escolheOperacao="evento => estado.operacao = evento.target.value" :number2="evento => estado.num.num2 = evento.target.value" />

  <h3>{{estado.num.num1}} {{ operacaoSymbol() }} {{estado.num.num2}} = {{ getOperacao() }}</h3>

  </div>
</template>

<style scoped>
</style>
