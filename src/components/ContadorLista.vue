<script lang="ts">
import type IItensToDo from '@/Interfaces/IItensToDo';
import type { PropType } from 'vue';

    export default{
        props:{
            ItensLista : { type: Array as PropType<IItensToDo[]>, required: true}
        },
        data(){
            return{

            }
        }
    }
</script>

<template>
    <div class="contador-lista">

        <div class="container-contador-tareas-criadas">
            <span class="titulo-tarefas-criadas">Tarefas criadas <p class="contador-tarefas-criadas">{{ ItensLista.length }}</p></span>
        </div>
        <div class="container-contador-tarefas-concluidas">
            <span class="titulo-tarefas-concluidas">Concluidas <p class="contador-tarefas-concluidas">{{ ItensLista.filter(it => it.status == true).length }} de {{ ItensLista.length }}</p></span>
        </div>
    </div>
</template>

<style scoped>

    .contador-lista{
        display: flex;
        align-items: center;
        justify-content: space-between;
        width: 42rem;
        height: 40px;
        border: none;
        margin: 0 auto;
        margin-top: 65px;
    }

    span{
        width: 10rem;
        display: flex;
        justify-content: space-between;
    }

    .titulo-tarefas-criadas{
        color: var(--blue-500);
    }

    .titulo-tarefas-concluidas{
        color: var(--purple-500);
    }

    .contador-tarefas-criadas, .contador-tarefas-concluidas{
        background-color: var(--gray-400);
        color: var(--gray-200);
        width: 20px;
        height: 20px;
        display: flex;
        justify-content: center;
        text-align: center;
        align-items: center;
        border-radius: 15px;
        font-size: 12px;
    }

    .contador-tarefas-concluidas{
        width: 60px;
    }
</style>