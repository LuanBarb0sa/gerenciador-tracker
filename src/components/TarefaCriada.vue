<template>
    <div class="box has-text-weigth-bold">
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao }}
            </div>
            <div class="column">
                <CronometroTarefas :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </div>
</template>
<script lang="ts">
import { defineComponent , PropType } from 'vue';
import CronometroTarefas from './CronometroTarefas.vue';
import ITarefa from '@/interfaces/ITarefa';
export default defineComponent({
    name: 'TarefaCriada',
    components: {
        CronometroTarefas
    },
    props: {
        tarefa: {
            type: Object as PropType <ITarefa>,
            required: true
        }
    }
})
</script>
<style scoped>
.box {
    background: #FAF0CA;
}
</style>