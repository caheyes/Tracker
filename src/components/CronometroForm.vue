<template>
    <section>
        <strong class="display">{{tempoDecorrido}}</strong>
    </section>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';

    export default defineComponent({
        name: 'CronometroForm',
        props: {
            tempoEmSegundos: {
                type: Number,
                default: 0
            }
        },
        computed: {
            tempoDecorrido() : string {
                //Transformando os segundos em horário habitual
                return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11, 8)
            }
        },
    })
</script>

<style scoped>
    .display {
        color: var(--texto-primario);
    }
</style>