<template>
    <form>
        <input type="text" name="busca" id="busca" v-model="busca">
        <input type="submit" value="Buscar" id="lupa" @click.prevent="buscarProdutos">
    </form>
</template>

<script>
    export default {
        name: "ProdutosBuscar",
        data() {
            return {
                busca: ""
            }
        },
        methods: {
            buscarProdutos() {
                this.$router.push({query: {q: this.busca}})
            }
        }
    }
</script>

<style scoped>

</style>
