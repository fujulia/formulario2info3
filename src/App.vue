<script setup>
import { ref, reactive } from 'vue'

const titulo = ref('Título')
const mostrarResultado = ref(false)
const produto = reactive({
  nome: 'Produto 1',
  preco: 0,
  quantidade: 10,
  categorias: []
})

function formatarPreco(preco) {
  return `R$ ${preco.toFixed(2).replace('.', ',')}`
}


</script>

<template>
  <h1>{{ titulo }}</h1>

  <div class="container">
    <div class="formulario">
      <h1>Formulario</h1>
      <input type="text" v-model="titulo" />
      <form @submit.prevent="mostrarResultado = !mostrarResultado">
      <div class="row">
        <label for="">Name:</label>
        <input type="text" v-model="produto.nome" required/>
      </div>
      <div class="row">
        <label for="">Preço:</label>
        <input type="number" v-model="produto.preco" />
      </div>
      <div>
        <label for="">Quantidade:</label>
        <input type="number" v-model="produto.quantidade" />
      </div>
      <button type="submit">Mostrar </button>
    </form>
    </div>
    <div v-if="mostrarResultado" class="resultado">
      <h1>Resultado</h1>
      <p>Nome: {{ produto.nome }}</p>
      <p>Preço: {{ formatarPreco(produto.preco) }}</p>
      <p>Quantidade: {{ produto.quantidade }}</p>
      <p>Categorias:{{ produto.categorias }}</p>
      <p>{{ mostrarResultado }}</p>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: row;
  gap: 1.5rem;
  width: 100vw;
}

.formulario,
.resultado {
  width: 45%;
  border-radius: 10px;
  padding: 10px;
}

.formulario {
  background-color: #c4c500;
}

.resultado {
  background-color: #c4c4c4;
}

.formulario .row {
  margin: 10px 20px;
  width: 70%;
  display: flex;
  justify-content: space-between;
}
</style>
