<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <CronometroForm :tempoEmSegundos="tempoEmSegundos"/>
        <BotaoTemporizador 
            @acaoBtn="iniciar" 
            :cronometroRodando="cronometroRodando" 
            :titulo="'play'"
            :icone="'fas fa-play'"
        />
        <BotaoTemporizador  
            @acaoBtn="finalizar" 
            :cronometroRodando="!cronometroRodando"
            :titulo="'stop'"
            :icone="'fas fa-stop'"
        />
    </div>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';
    import CronometroForm from './CronometroForm.vue';
    import BotaoTemporizador from './BotaoTemporizador.vue';

    export default defineComponent({
        name: 'TemporizadorControle',
        emits: ['aoTemporizadorFinalizado'],
        components: {
            CronometroForm,
            BotaoTemporizador
        },
        data() {
            return {
                tempoEmSegundos: 0,
                cronometro: 0,
                cronometroRodando: false
            }
        },
        methods: {
            iniciar() {
                //começar a contagem, ficará contando e acrescentando sempre mais 1
                this.cronometroRodando = true;
                this.cronometro = setInterval(() => {
                    this.tempoEmSegundos += 1;
                }, 1000);
            },
            finalizar() {
                this.cronometroRodando = false;
                clearInterval(this.cronometro);
                this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
                this.tempoEmSegundos = 0;
            }
        }
    });
</script>