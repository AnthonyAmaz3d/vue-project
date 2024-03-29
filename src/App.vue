<script setup>
import { reactive, ref, watch } from 'vue';

const estado = reactive({
  resultado: 0,
})

const numero1 = ref(0)
const numero2 = ref(0)
const filter = ref("")

const trocaFiltro = () => {
  switch (filter.value) {
  case "adicao":
    somar(numero1.value, numero2.value);
    break
  case "subtracao":
    diminuir(numero1.value, numero2.value);
    break
  case "multiplicacao":
    multiplicar(numero1.value, numero2.value);
    break
  case "divisao":
    dividir(numero1.value, numero2.value);
    break
}}

const somar = (numero1, numero2) => {
  estado.resultado = numero1 + numero2;
}

const diminuir = (numero1, numero2) => {
  estado.resultado = numero1 - numero2;
}

const multiplicar = (numero1, numero2) => {
  estado.resultado = numero1 * numero2;
}

const dividir = (numero1, numero2) => {
  estado.resultado = numero1 / numero2;
}

watch([numero1, numero2, filter], () => {
  if (filter.value) {
    trocaFiltro();
  }
})
</script>

<template>
  <div class="container mb-4 mt-4 bg-secondary pt-2 rounded-3">
    <header class="mb-4">
      <h1>Calculador em Vue</h1>
    </header>
    <div class="row">
      <div class="col-3">
        <input class="form-control" type="number" placeholder="Digite o primeiro número" v-model.number="numero1">
      </div>
      <div class="col-2">
        <select v-model="filter" class="form-select">
          <option value="0"></option>
          <option value="adicao">Adição(+)</option>
          <option value="subtracao">Subtração(-)</option>
          <option value="multiplicacao">Multiplicação(*)</option>
          <option value="divisao">Divisão(/)</option>
        </select>
      </div>
      <div class="col-3">
        <input class="form-control" type="number" placeholder="Digite o segundo número" v-model.number="numero2">
      </div>
      <div class="col-1">
        <p class="form-control">
          Resultado:
        </p>
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
