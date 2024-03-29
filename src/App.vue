<script setup>
import { reactive } from 'vue';

const estado = reactive({
  resultado: 0,
})

let numero1 = 0
let numero2 = 0
let filter = "0"

const adicionaNumero1 = (evento) => {
  numero1 = parseInt(evento.target.value);
}

const valorSelect = (evento) => {
  filter = evento.target.value;
}

const adicionaNumero2 = (evento) => {
  numero2 = parseInt(evento.target.value);
}

const trocaFiltro = () => {
  switch (filter) {
  case "adicao":
    return somar(numero1, numero2);
  case "subtracao":
    return diminuir(numero1, numero2);
  case "multiplicacao":
    return multiplicar(numero1, numero2);
  case "divisao":
    return dividir(numero1, numero2);
}}

const somar = (numero1, numero2) => {
  return estado.resultado = numero1 + numero2;
}

const diminuir = (numero1, numero2) => {
  return estado.resultado = numero1 - numero2;
}

const multiplicar = (numero1, numero2) => {
  return estado.resultado = numero1 * numero2;
}

const dividir = (numero1, numero2) => {
  return estado.resultado = numero1 / numero2;
}
</script>

<template>
  <div class="container mb-4 mt-4 bg-secondary pt-2 rounded-3">
    <header class="mb-4">
      <h1>Calculador em Vue</h1>
    </header>
    <div class="row">
      <div class="col-3">
        <input class="form-control" type="number" placeholder="Digite o primeiro número" @keyup="adicionaNumero1">
      </div>
      <div class="col-2">
        <select @change="valorSelect" class="form-select">
          <option value="0"></option>
          <option value="adicao">Adição(+)</option>
          <option value="subtracao">Subtração(-)</option>
          <option value="multiplicacao">Multiplicação(*)</option>
          <option value="divisao">Divisão(/)</option>
        </select>
      </div>
      <div class="col-3">
        <input class="form-control" type="number" placeholder="Digite o segundo número" @keyup="adicionaNumero2">
      </div>
      <div class="col">
        <button @click="trocaFiltro" class="btn btn-dark">Calcular</button>
      </div>
      <div class="col">
        <p class="form-control" placeholder="Resultado:">
          {{ estado.resultado }}
        </p>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>
