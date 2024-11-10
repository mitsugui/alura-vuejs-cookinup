<script lang="ts">
export default {
    props: {
        receita: {
            type: Object,
            required: true
        }
    }
}
</script>

<template>
    <article class="card-receita">
        <header>
            <img :src="`/imagens/receitas/${receita.imagem}`" alt="">

            <h2 class="paragrafo-lg receita__nome">{{ receita.nome }}</h2>
        </header>
    </article>
</template>

<style scoped>
</style>