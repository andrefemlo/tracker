<template>
  <main class="columns is-gapless is-multiline" :class="{ 'darkmode': activeDarkMode }">
    <div class="column is-one-quarter">
      <BarraLateral @inThemeChange="changeTheme"/>

    </div>
    <div class="column is-tree-quarter conteudo">
      <FormularioPrincipal @aoSalvarTarefa="salvarTarefa"/>

      <div class="tarefas">
        <TarefaRealizada v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        <BoxWrapper v-if="listaVazia">
          Você ainda não tem nenhuma tarefa cadastrada.
        </BoxWrapper>
      </div>

    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioPrincipal from './components/FormularioPrincipal.vue';
import TarefaRealizada from "./components/TarefaRealizada.vue";
import ITarefa from "./interfaces/ITarefa";
import BoxWrapper from './components/Box.vue';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioPrincipal,
    TarefaRealizada,
    BoxWrapper
},
  data () {
      return {
        tarefas: [] as ITarefa[],
        activeDarkMode: false
      }
  },
  computed: {
    listaVazia () : boolean {
      return this.tarefas.length === 0;
    }
  },
  methods: {
    salvarTarefa (tarefa: ITarefa){
      this.tarefas.push(tarefa)
    },
    changeTheme (activeDarkMode: boolean) {
      this.activeDarkMode = activeDarkMode

    }
  }
});
</script>

<style scoped>
main{
  --bg-primary: #f2f2f2;
  --text-primary: #303032;
}
main.darkmode{
  --bg-primary: #2b2b42;
  --text-primary: #ddd;
}

.conteudo{
  background-color: var(--bg-primary);
}

.tarefas{
  padding: 1rem 2rem;
}
</style>
