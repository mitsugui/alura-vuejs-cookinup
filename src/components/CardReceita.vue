<script lang="ts">
import type IReceita from '@/interfaces/IReceita';
import type { PropType } from 'vue';

export default {
    props: {
        receita: {
            type: Object as PropType<IReceita>,
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