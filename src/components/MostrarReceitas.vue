<script lang="ts">
import { obterReceitas } from '@/http/index';
import type IReceita from '@/interfaces/IReceita';
import CardReceita from './CardReceita.vue';
import BotaoPrincipal from './BotaoPrincipal.vue';

export default {
    components: {
        BotaoPrincipal,
        CardReceita
    },
    data() {
        return {
            receitas: [] as IReceita[]
        }
    },
    emits: ['editarLista'],
    async created() {
        this.receitas = await obterReceitas();
    }
}
</script>

<template>
    <section class="mostrar-receitas">
        <h1 class="cabecalho titulo-receitas">Receitas</h1>

        <p class="paragrafo-lg instrucoes">
            Resultados encontrados: {{ receitas.length }}
        </p>

        <p v-if="receitas.length" class="paragrafo-lg instrucoes">
            Veja as opções de receitas que encontramos com os ingredientes que você tem por aí!
        </p>
        <p v-else class="paragrafo-lg instrucoes">
            Ops, não encontramos resultados para sua combinação. Vamos tentar de novo?
        </p>

        <ul v-if="receitas.length" class="receitas">
            <li v-for="receita in receitas" :key="receita.nome">
                <CardReceita :receita="receita" />
            </li>
        </ul>
        <img v-else src="../assets/images/sem-receitas.png" alt="Sem resultados" />

        <BotaoPrincipal :texto="'Editar lista'" @click="$emit('editarLista')" />
    </section>
</template>

<style scoped>
.mostrar-receitas {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.titulo-receitas {
    color: var(--verde-medio, #3D6D4A);
    display: block;
    margin-bottom: 1.5rem;
}

.instrucoes {
    margin-bottom: 2rem;
}

.receitas {
    margin-bottom: 1rem;
    display: flex;
    justify-content: center;
    gap: 1.5rem;
    flex-wrap: wrap;
    list-style-type: none;
}

@media only screen and (max-width: 767px) {
    .dica {
        margin-bottom: 2.5rem;
    }
}
</style>