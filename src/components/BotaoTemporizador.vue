<template>
    <button class="button" @click="acaoBtn" :disabled="cronometroRodando">
            <span class="icon">
            <i :class="icone"></i>
        </span>
        <span>{{titulo}}</span>
    </button>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';

    export default defineComponent({
        name: 'BotaoTemporizador',
        emits: ['acaoBtn'],
        props: {
            cronometroRodando: {
                type: Boolean,
            },
            titulo: {
                type: String,
                required: true
            },
            icone: {
                type: String,
                required: true
            }
        },
        methods: {
            acaoBtn() {
                this.$emit('acaoBtn');
            }
        }
    })
</script>