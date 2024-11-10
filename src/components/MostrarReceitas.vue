<script lang="ts">
import BotaoPrincipal from './BotaoPrincipal.vue';
import CardReceita from './CardReceita.vue';

export default {
    components: {
        BotaoPrincipal,
        CardReceita
    },
    data() {
        return {
            receitas: [
                {
                    nome: 'Pasta de alho assado',
                    imagem: 'pasta_de_alho_assado.png'
                },
                {
                    nome: 'Patê de alho assado',
                    imagem: 'pate_de_alho_assado.png'
                }
            ]
        }
    },
    emits: ['editarLista']
}
</script>

<template>
    <section class="mostrar-receitas">
        <h1 class="cabecalho titulo-receitas">Receitas</h1>

        <p class="paragrafo-lg instrucoes">
            Resultados encontrados: 8
        </p>

        <p class="paragrafo-lg instrucoes">
            Veja as opções de receitas que encontramos com os ingredientes que você tem por aí!
        </p>


        <ul class="receitas">
            <li v-for="receita in receitas" :key="receita.nome">
                <CardReceita :receita="receita" />
            </li>
        </ul>

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
</style>