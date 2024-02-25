<template>
    <BoxWrapper>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricaoDaTarefa || 'Tarefa sem Descrição' }}
            </div>
            <div class="column">
                <CronometroTarefa :tempoEmSegundos="tarefa.duracaoEmSegundos" />
            </div>
        </div>
    </BoxWrapper>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import CronometroTarefa from './CronometroTarefa.vue';
import BoxWrapper from './Box.vue';
import ITarefa from "@/interfaces/ITarefa";

export default defineComponent({
    name: 'TarefaRealizada',
    components: {
        CronometroTarefa,
        BoxWrapper
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true,
        }
    }
})
</script>