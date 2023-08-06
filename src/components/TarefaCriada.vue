<template>
    <BoxTarefa>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <CronometroTarefas :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </BoxTarefa>
</template>
<script lang="ts">
import { defineComponent , PropType } from 'vue';
import CronometroTarefas from './CronometroTarefas.vue';
import ITarefa from '@/interfaces/ITarefa';
import BoxTarefa from './BoxTarefa.vue';
export default defineComponent({
    name: 'TarefaCriada',
    components: {
        CronometroTarefas,
        BoxTarefa
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