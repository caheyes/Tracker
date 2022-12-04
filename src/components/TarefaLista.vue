<template>
    <Box>
        <div class="columns">
            <div class="column is-7">
                {{tarefa.descricao || 'Tarefa sem descrição'}}
            </div>
            <div class="column">
                <CronogramaForm :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </Box>
</template>

<script lang="ts">
    import { defineComponent, PropType } from 'vue';
    import CronogramaForm from './CronometroForm.vue';
    import Box from './Box.vue';
    import ITarefa from '@/interfaces/ITarefas';

    export default defineComponent({
        name: 'TarefaLista',
        components: {
            CronogramaForm,
            Box
        },
        props: {
            tarefa: {
                type: Object as PropType<ITarefa>, //Mostrando que o tipo é um obj do ITarefa
                required: true //é obrigatorio
            }
        }
    })
</script>