<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa deseja iniciar ?"
          v-model="descricao"
        />
      </div>
      <div class="column">
        <TemporizadorTarefas @ao-temporizador-finalizado="finalizarTarefa" />
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";
import TemporizadorTarefas from "../components/TemporizadorTarefas.vue";
export default defineComponent({
  name: "FormulárioTarefas",
  components: {
    TemporizadorTarefas,
  },
  data () {
    return {
      descricao: ''
    }
  },
  methods: {
    finalizarTarefa (tempoDecorrido: number) : void {
      console.log('tempo da tarefa ' + tempoDecorrido);
      console.log('titulo tarefa' + this.descricao);
      this.descricao = ''
    },
  },
});
</script>
<style></style>
