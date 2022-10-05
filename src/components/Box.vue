<template>
    <div class="box has-text-wheight-bold">
        <slot></slot>              
    </div>
</template>

<script lang="ts">
import { defineComponent} from 'vue';

export default defineComponent({
    name:'BaseBox'
})

</script>

<style scoped>
   
       .box{
           background:#faf0ca;
       }
</style>