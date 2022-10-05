<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro':modoEscuroAtivo}">

    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema" />
    </div>
    <div class="column is-three-quarter">
     <BaseFormulario @aoSalvarTarefa="salvarTarefa" />
     <div class="lista">
     <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
  <BaseBox v-if="listaEstaVazia">
     Você  não esta muito produtivo hoje :(
  </BaseBox>
     </div>
    </div>
  </main>

</template>

<script lang="ts">
  import {
    defineComponent
  } from 'vue';
  import BarraLateral from './components/barraLateral.vue';
  import BaseFormulario from './components/Formulario.vue';
import Tarefa from './components/Tarefa.vue';
import BaseBox from './components/Box.vue';
import ITarefas from './interfaces/ITarefas';


  export default defineComponent({
    name: "App",
    components: {
      BarraLateral,
      BaseFormulario,
      Tarefa,
      BaseBox,
       },
      data(){
        return{
          tarefas: [] as ITarefas[],
          modoEscuroAtivo:false
        }
      },
      computed:{
          listaEstaVazia () : boolean{
            return this.tarefas.length === 0
          }
      },
    methods:{
      salvarTarefa (tarefa:ITarefas){
        this.tarefas.push(tarefa)
      },
      trocarTema (modoEscuroAtivo: boolean){
           this.modoEscuroAtivo = modoEscuroAtivo
      }
    }
  });
</script>

<style scoped>

 .lista{
    padding: 1.25rem;
  }
.columns{
  margin-left:0.25rem;
}
</style>