<template>
  <section>
    <h1> 👍 Compre ou Venda <span class="flip">👍</span> </h1>
    <ProdutosBuscar/>
    <ProdutosLista/>
  </section>
</template>

<script>
// @ is an alias to /src
import ProdutosBuscar from "@/components/ProdutosBuscar";
import ProdutosLista from "@/components/ProdutosLista";
export default {
  name: 'Home',
  components: {
    ProdutosBuscar,
    ProdutosLista,
  }
}
</script>
<style scoped>
  h1 {
    color: #87f;
    margin-top: 40px;
    font-size: 2rem;
    text-align: center;
  }
  .flip {
    display: inline-block;
    -moz-transform: scale(-1, 1);
    -webkit-transform: scale(-1, 1);
    -o-transform: scale(-1, 1);
    -ms-transform: scale(-1, 1);
    transform: scale(-1, 1);
  }
</style>
