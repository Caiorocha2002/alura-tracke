<template>
    <div class="is-flex is align-items-center is-justify-content-space-between">
        <cronometro :tempoEmSegundos="tempoEmSegundos" />
        <button class="button" @click="goPlay" :disabled="cronometroRodando">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>
        <button class="button" @click="stopStop" :disabled="!cronometroRodando">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
    </div>

</template>
<script lang="ts">
    import {
        defineComponent
    } from "vue";
    import cronometro from './cronometro.vue'

    export default defineComponent({
        name: 'temporizadorBase',
        emits:['aoTemporizadorFinalizado'],
        components: {
            cronometro
        },
        data() {
            return {
                tempoEmSegundos: 0,
                cronometro: 0,
                cronometroRodando: false
            }
        },

        methods: {
            goPlay() {
                this.cronometroRodando = true
                this.cronometro = setInterval(() => {
                    this.tempoEmSegundos++
                }, 1000)

            },
            stopStop() {
                  this.cronometroRodando = false
                clearInterval(this.cronometro)
                this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
                this.tempoEmSegundos =0
            }
        }
    });
</script>