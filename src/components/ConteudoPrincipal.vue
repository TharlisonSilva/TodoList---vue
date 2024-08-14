<script lang="ts">
    import type IItensToDo from '@/Interfaces/IItensToDo';
    import ContadorLista from './ContadorLista.vue';
    import ListaPrincipal from './ListaPrincipal.vue';
    import Cabecalho from './Cabecalho.vue';  
    import { v4 as uuidv4 } from 'uuid';
  
    export default {
        data(){
            return {
                ItensLista : [] as IItensToDo []        
            }
        }, 
        components: { ContadorLista, ListaPrincipal, Cabecalho },
        methods: {
            removerItem(idItem : String){
                this.ItensLista = this.ItensLista.filter(item => item.id != idItem);
            },
            adicionarItem(mensagem : String){
                const item: IItensToDo = {
                    id: uuidv4(),
                    Mensagem: mensagem,
                    status: false
                };
                this.ItensLista.push(item);
                console.log(this.ItensLista);
            },
            concluirTarefa(idItem : String){
                this.ItensLista.filter(x => x.id === idItem).forEach(x => x.status = !x.status);
            }
        },
        mounted() {
            
        }
    }

</script>

<template>
    <Cabecalho @IncluirItemInput="adicionarItem"/>
    <div class="container-principal">
        <ContadorLista :ItensLista="ItensLista"/>    
        <ListaPrincipal :ItensLista="ItensLista" @excluir-item="removerItem" @concluir-tarefa="concluirTarefa"/>         
    </div>
</template>


<style scoped>
    .container-principal{
        width: 100%;
        height: 100%;
    }

</style>