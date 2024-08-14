<script lang="ts">
    import { PhPlusCircle } from "@phosphor-icons/vue";
    export default{
        emits: ['IncluirItemInput'],
        methods: {
            EmitirItemInput(){
                const inputElement = document.querySelector<HTMLInputElement>('#inputValue');
                this.$emit('IncluirItemInput', inputElement?.value);
            }
        },
        components: { PhPlusCircle },
        mounted(){
            const InputValue = document.getElementById('inputTarefa');
            console.log(InputValue?.textContent);
        }

    }
</script>

<template>
    <header class="header-site">
        <div class="logo-site-name">
            <div class="container-logo">
                <img src="../assets/icons/logo.png" alt="icone do todo list com formato de foguete" class="logo-site-img" />
            </div>
        </div>

        <div class="container-incluir">
            <input type="text" class="input-incluir" placeholder="Adicione uma nova tarefa" id="inputValue"/>
            <button class="salvar-item" @click.prevent="EmitirItemInput()">
                <p>Criar</p>
                <PhPlusCircle :size="16" color="White" />
            </button>
        </div>
    </header>
</template>

<style scoped>
    .header-site{
        background-color: var(--gray-700);
        width: 100%;
        height: 250px;
    }

    .logo-site-name{
        width: 100%;
        height: 250px;
        display: flex;
        align-content: center;
        align-items: center;
        justify-content: center;
    }

    .container-logo{
        height: 48px;
        display: flex;
        align-items: center;
    }

    .container-incluir{
        margin-top: -1.2rem;
        width: 100%;
        height: 38px;
        display: flex;
        justify-content: center;
    }

    .input-incluir{
        width: 37rem;
        border-radius: 8px;
        border: none;
        color: var(--gray-300);
        background-color: var(--gray-500);
        padding-left: 10px;
        margin-right: 5px;
    }

    .salvar-item{
        background-color: var(--blue-500);
        width: 4.5rem;
        height: 38px;
        border: none;
        border-radius: 5px;
        color: var(--gray-100);
        align-items: center;
        text-align: center;
        justify-content: center;
        display: flex;
        cursor: pointer;
    }

    .salvar-item:focus{
        outline: transparent;
    }

    .salvar-item > p{
        margin-right: 5px;
    }

</style>