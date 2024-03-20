<script setup>
import { reactive } from 'vue';

const estado = reactive({
  resultado: 0,
  filter: "adicao",
})

const adicionaNumero1 = (evento) => {
  const numero1 = evento.target.value;
  console.log(numero1)
}

const adicionaNumero2 = (evento) => {
  const numero2 = evento.target.value
  console.log(numero2)
}

const trocarOperacao = () => {
  const { filter } = estado;
    switch(filter) {
      case 'subtracao':
        return diminuir();
      case 'multiplicacao':
        return multiplicar();
      case 'divisao':
        return dividir();
      default:
        return somar();
    }
}

const somar = () => {
  estado.resultado = numero1 + numero2;
}

const diminuir = () => {
  estado.resultado = numero1 - numero2;
}

const multiplicar = () => {
  estado.resultado = numero1 * numero2;
}

const dividir = () => {
  estado.resultado = numero1 / numero2;
}

</script>

<template>
  <div class="container mb-4 mt-4 bg-secondary pt-2 ">
    <header class="mb-4">
      <h1>Calculador em Vue</h1>
    </header>

    <div class="row">
      <div class="col-3">
        <input class="form-control" type="number" placeholder="Digite o primeiro número" @keyup="adicionaNumero1">
      </div>
      <div class="col-2">
        <select class="form-select" @change="trocarOperacao()">
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
        <button class="btn btn-dark">Calcular</button>
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
