<script lang="ts">
    import type IItensToDo from "@/Interfaces/IItensToDo";
    import type { PropType } from "vue";
    import { PhTrash } from "@phosphor-icons/vue";
    
    export default{
        props:{
            ItensLista : { type: Array as PropType<IItensToDo[]>, required: true}
        },
        data(){
            return{

            }
        },
        components:{ PhTrash },
        methods:{
            concluirTarefa(idCard : String){
                this.$emit('ConcluirTarefa', idCard);
            },
            excluirTarefa(idCard : String){
                this.$emit('ExcluirItem', idCard);
            }
        },
        emits:['ExcluirItem', 'ConcluirTarefa'],
    }
</script>

<template>
    <div class="container-lista-itens">
        <ul class="lista-items">
            <li v-for="item in ItensLista" key="item.id" id="itemLista-{{item.id}}" class="item-lista">
                <input type="checkbox" class="check-item" @click.prevent="concluirTarefa(item.id)" v-if="item.status" checked />
                <input type="checkbox" class="check-item" @click.prevent="concluirTarefa(item.id)" v-else />
                <span class="descricao-item">{{item.Mensagem}}</span>
                <PhTrash :size="20" color="gray" class="button-excluir" @click.prevent="excluirTarefa(item.id)"/>
            </li>
        </ul>
    </div>
</template>

<style scoped>
    .container-lista-itens{
        width: 44rem;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        align-content: center;
        margin: 0 auto;
        border: none;
        border-radius: 8px;
        border-top: 1px solid var(--gray-400);
        margin-top: 5px;

    }

    .lista-items{
        display: flex;
        width: 45rem;
        height: 100%;
        align-items: center;
        justify-content: center;
        text-align: center;
        flex-direction: column;
        margin-top: 20px;
    }

    .item-lista{
        width: 42rem;
        height: 45px;
        display: flex;
        align-items: center;
        justify-content: space-evenly;
        background-color: var(--gray-400);
        padding: 10px;
        margin-bottom: 10px;
        color: var(--gray-100);
        text-align: left;
        font-size: 0.8rem;
        border-radius: 8px;
    }

    .item-lista span{
        width: 90%;
        padding: 5px;
    }

    .button-excluir{
        cursor: pointer;
    }

    .button-excluir:hover{
        fill: var(--red-500);
    }

    .check-item{
        width: 1rem;
        height: 1rem;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        border-radius: 50%;
        vertical-align: middle;
        border: 1px solid var(--purple-500);
    }

    .check-item img{
        width: 10px;
        height: 10px;
        color: var(--white-500);
        display: none;
    }

    .showCheck{
        display: block;
    }

    .showBackgroudCheck{
        background-color: var(--purple-500);
        border-color: var(--purple-500);
    }

    .item-confirmado{
        fill: var(--blue-500);
    }

    .item-confirmado:hover{
        cursor: pointer;
    }



</style>