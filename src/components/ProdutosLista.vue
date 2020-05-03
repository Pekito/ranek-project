<template>
  <section class="produtos-container">
    <div v-if="produtos && produtos.length > 0" class="produtos">
      <div class="produto" v-for="produto in produtos" :key="produto.id">
        <router-link to="/">
          <img
            v-if="produto.fotos"
            :src="produto.fotos[0].src"
            :alt="produto.fotos[0]"
          />
          <h2 class="titulo">{{ produto.nome }}</h2>
          <p class="preco">{{ produto.preco }}</p>
          <p>{{ produto.descricao }}</p>
        </router-link>
      </div>
    </div>
    <div class="invalido" v-else-if="produtos && produtos.length === 0">
      <p>Busca sem resultados, tente buscar outro termo.</p>
    </div>
  </section>
</template>

<script>
import { api } from "@/services.js";
import { serialize } from "@/helpers";

export default {
  name: "ProdutosLista",
  data() {
    return {
      produtos: null,
      pagination: 9,
    };
  },
  methods: {
    getProdutos() {
      api.get(this.url).then((resposta) => (this.produtos = resposta.data));
    },
  },
  created() {
    this.getProdutos();
  },
  watch: {
    url() {
      this.getProdutos();
    },
  },
  computed: {
    url() {
      const query = serialize(this.$route.query);
      return `/produto/?_limit=${this.pagination}${query}`;
    },
  },
};
</script>

<style scoped>
.produtos-container {
  max-width: 1000px;
  margin: 0 auto;
}
.produtos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-grap: 30px;
  margin: 30px;
}
.produto {
  box-shadow: 0 4px 8px rgba(30, 60, 90, 0.1);
  padding: 10px;
  background: #fff;
  border-radius: 4px;
  transition: all 0.2s;
}
.produto:hover {
  box-shadow: 0 6px 12px rgba(30, 60, 90, 0.1);
  transform: scale(1.1);
  position: relative;
  z-index: 1;
}
.produto img {
  border-radius: 4px;
  margin-bottom: 20px;
}
.titulo {
  margin-bottom: 20px;
}
.preco {
  color: #e80;
  font-weight: bold;
}
.invalido {
  text-align: center;
}
</style>
