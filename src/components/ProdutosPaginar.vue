<template>
  <ul v-if="paginas > 1">
    <li v-if="$route.query._page > 0"><router-link :to="{ query: query($route.query._page - 1) }"> ⬅ </router-link></li>
    <li v-for="pagina in range" :key="pagina">
      <router-link :to="{ query: query(pagina) }">
        {{ pagina }}
      </router-link>
    </li>
      <li v-if="$route.query._page < paginas"><router-link :to="{ query: query($route.query._page + 1) }"> ➡ </router-link></li>
  </ul>
</template>

<script>
export default {
  name: "ProdutosPaginar",
  props: {
    produtosPorPagina: {
      type: Number,
      default: 1,
    },
    produtosTotal: {
      type: Number,
      default: 1,
    },
  },
  computed: {
    range() {
      const current = this.$route.query._page
        ? Number(this.$route.query._page)
        : 1;
      const range = 9;
      const offset = Math.ceil(range / 2);
      const total = this.paginas;
      const pagesArray = [];
      for (let i = 1; i <= total; i++) {
        pagesArray.push(i);
      }
      pagesArray.splice(0, current - offset);
      pagesArray.splice(range, total);
      return pagesArray;
    },
    paginas() {
      const total = this.produtosTotal / this.produtosPorPagina;
      return total !== Infinity ? Math.ceil(total) : 0;
    },
  },
  methods: {
    query(pagina) {
      return {
        ...this.$route.query,
        _page: pagina,
      };
    },
  },
};
</script>

<style scoped>
ul {
  grid-column: 1 / -1;
}
li {
  display: inline-block;
}
li a {
  padding: 2px 8px;
  border-radius: 2px;
  margin: 4px;
}
li a.router-link-exact-active,
li a:hover {
  background: #8877ff;
  color: #fff;
}
</style>
