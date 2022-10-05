<template>
   <BaseBox>
      <div class="columns">
       <div class="columns is-7">
         {{tarefa.descricao || 'Tarefa sem descrição'}}
       </div>
       <div class="column">
       <cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
       </div>
      </div>
   </BaseBox>
</template>
<style scoped>

</style>

<script lang="ts">
import { defineComponent, PropType} from 'vue'
import cronometro from './cronometro.vue';
import ITarefas from '../interfaces/ITarefas';
import BaseBox from './Box.vue';
export default defineComponent({
    name:'nameTarefa',
    components:{
        cronometro,
        BaseBox
    },
    props:{
        tarefa:{
            type:Object as PropType <ITarefas>,
            required:true
        }
    }
})
</script>