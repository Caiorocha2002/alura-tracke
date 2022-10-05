<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulario de tarefa">
                <input type="text" class="input" placeholder="qual tarefa deseja iniciar?" v-model="descricao">
            </div>
            <div class="column">
           <temporizadorBase @aoTemporizadorFinalizado="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
 import {
        defineComponent} from "vue";
    import temporizadorBase from './temporoizador.vue';

    export default defineComponent({
        name: 'BaseFormulario',
        emits:['aoSalvarTarefa'],
        components: {
           temporizadorBase
        },
        data (){
            return{
                descricao:''
            }
        },
        methods:{
            finalizarTarefa (tempoDecorrido: number): void{
                this.$emit('aoSalvarTarefa', {
                    duracaoEmSegundos: tempoDecorrido,
                    descricao:this.descricao
                })
                  this.descricao=''
            }
        }
        });
</script>
<style>
    .columns{
        margin-left:0.25rem;
        
    }
</style>