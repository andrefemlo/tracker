<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa.">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="descricaoDaTarefa">
            </div>
            <div class="column">
                <TemporizadorTarefas @aoTemporizadorFinalizado="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TemporizadorTarefas from './Temporizador.vue';

export default defineComponent({
    name: 'FormularioPrincipal',
    components: {
        TemporizadorTarefas
    },
    emits: ['aoSalvarTarefa'],
    data () {
        return {
            descricaoDaTarefa: ''
        }
    },
    methods: {
        finalizarTarefa(tempoDecorrido: number) :void {
            this.$emit('aoSalvarTarefa', {
                duracaoEmSegundos: tempoDecorrido,
                descricaoDaTarefa: this.descricaoDaTarefa
            });
            this.descricaoDaTarefa = '';
        }
    }
})
</script>

<style>
.formulario{
    color: var(--text-primary);
    background-color: var(--bg-primary);
}
</style>