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
    <article class="receita">
        <header>
            <img :src="`/imagens/receitas/${receita.imagem}`" alt="" class="imagem">

            <h2 class="paragrafo receita__nome">{{ receita.nome }}</h2>
        </header>
    </article>
</template>

<style scoped>
.receita {
    width: 17.625rem;
    border-radius: 1rem;
    background: var(--branco, #FFF);
    box-shadow: 4px 4px 10px 0px rgba(68, 68, 68, 0.05);
    height: 14.75rem;

    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 2rem;
}

.imagem {
    border-radius: 1rem 1rem 0 0;
    display: block;
    max-width: 17.625rem;
    max-height: 9.375rem;
    width: 17.625rem;
    height: 9.375rem;
}

.receita__nome {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 5.375rem;
    font-weight: 300;
}
</style>