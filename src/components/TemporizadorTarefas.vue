<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <CronometroTarefas :tempoEmSegundos="tempoEmSegundos" />
    <button class="button ml-3" @click="iniciar" :disabled="cronometroRodando">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button ml-3" @click="finalizar" :disabled="!cronometroRodando">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";
import CronometroTarefas from '../components/CronometroTarefas.vue'
export default defineComponent({
  name: "TemporizadorTarefas",
  emits: ['aoTemporizadorFinalizado'],
  components: {
    CronometroTarefas
  },
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      cronometroRodando: false
    };
  },
  methods: {
    iniciar() {
    this.cronometroRodando = true
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos++;
      }, 1000);
    },
    finalizar() {
        this.cronometroRodando = false
      clearInterval(this.cronometro)
      this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
      this.tempoEmSegundos = 0
    },
  },
});
</script>
<style></style>
