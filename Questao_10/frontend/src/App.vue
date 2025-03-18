<template>
  <div id="app">
    <h1>Produtos</h1>
    <div v-for="produto in produtos" :key="produto.id">
      <h2>{{ produto.nome }}</h2>
      <p>{{ produto.descricao }}</p>
      <p>{{ produto.preco }}</p>
      <img :src="'/storage/' + produto.imagem" alt="Imagem do produto" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      produtos: []
    }
  },
  created() {
    this.$http.get('http://localhost:8000/api/produtos').then(response => {
      this.produtos = response.data;
    });
  }
}
</script>

<style>

</style>
