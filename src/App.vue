<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral/>
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioTarefas @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <TarefaCriada v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        <BoxTarefa v-if="listaEstaVazia">
          Você não está muito produtivo hoje :(
        </BoxTarefa>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import BarraLateral from './components/BarraLateral.vue'
import FormularioTarefas from './components/FormularioTarefas.vue'
import TarefaCriada from './components/TarefaCriada.vue'
import ITarefa from './interfaces/ITarefa'
import BoxTarefa from './components/BoxTarefa.vue'
export default defineComponent({
  name: 'App',
   components: {
    BarraLateral,
    FormularioTarefas,
    TarefaCriada,
    BoxTarefa
},
   data () {
    return {
      tarefas: [] as ITarefa []
    }
   },
   computed: {
    listaEstaVazia () : boolean {
      return this.tarefas.length === 0
    }
   },
   methods: {
    salvarTarefa (tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    }
   }
});
</script>

<style>
.lista {
  padding: 1.25rem;
}

main {
  --bg-primario: #fff;
  --texto-primario: #000;
}
main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}
.conteudo {
  background-color: var(--bg-primario);
}
</style>
./interfaces/ITarefa