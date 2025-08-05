<script setup>
import { reactive } from "vue";

const resultado = reactive({
  valorA: "",
  valorB: "",
  operacao: "add",
});

function somar() {
  const n1 = parseFloat(resultado.valorA);
  const n2 = parseFloat(resultado.valorB);
  if (isNaN(n1) || isNaN(n2)) {
    resultado.valorFinal = "Erro: Insira valores numéricos.";
    return;
  }
  if (resultado.operacao === "add") {
    return (resultado.valorFinal = n1 + n2);
  } else if (resultado.operacao === "sub") {
    return (resultado.valorFinal = n1 - n2);
  } else if (resultado.operacao === "mult") {
    return (resultado.valorFinal = n1 * n2);
  } else if (resultado.operacao === "divi") {
    if (n2 !== 0) {
      return (resultado.valorFinal = n1 / n2);
    } else {
      return (resultado.valorFinal = "Erro: Divisão por zero.");
    }
  }
}
</script>

<template>
  <div class="container">
    <h1 class="title">Calculadora Aritmética</h1>
    <br />
    <form>
      <label for="n-1">Digite o primeiro valor</label>
      <input id="n-1" type="number" v-model.number="resultado.valorA" />
      <label for="n-2">Digite o segundo valor</label>
      <input id="n-2" type="number" v-model.number="resultado.valorB" />
      <select name="Operacao" id="Operacao" v-model="resultado.operacao">
        <option value="add">Adição</option>
        <option value="sub">Subtração</option>
        <option value="mult">Multiplicação</option>
        <option value="divi">Divisão</option>
      </select>
    </form>
    <h1>
      O resultado será:
      <p class="title">{{ somar() }}</p>
    </h1>
  </div>
</template>

<style scoped></style>
