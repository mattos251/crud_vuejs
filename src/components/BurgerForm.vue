<template>
  <div id="main-form">

    <div>
        <form id="burger-form">
            <div class="input-container">
                <label for="nome">Nome do cliente: </label>
                <input type="text" id="nome" name="nome" v-model="nome" placeholder=" Digite aqui seu nome">
            </div>

            <div class="input-container">
                <label for="pao"> Escolha seu pão: </label>

                <select name="pao" id="pao" v-model="pao">
                    <option value="">Selecione seu pao</option>
                    <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">
                        {{pao.tipo}}
                    </option>                    
                </select>

            </div>

            <div class="input-container">
                <label for="carne" > Escolha a carne do seu burger: </label>

                <select name="carne" id="carne" v-model="carne">
                    <option value="">Selecione o tipo de carne</option>
                    <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{carne.tipo}}</option>
                </select>

            </div>

            <div id="opcionais-container" class="input-container">
                <label id="opcionais-title" for="opcionais" placeholder=""> Selecione outras opções: </label>

                <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id" >
                    <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
                    <span> {{opcional.tipo}}</span>
                </div>

                <div class="checkbox-container" >
                     <input type="checkbox" name="opcionais" v-model="opcionais" value="opcionais">
                    <span> Bacon</span>
                </div>  
                
                <div class="checkbox-container">
                    <input type="checkbox" name="opcionais" v-model="opcionais" value="opcionais">
                    <span> Cheddar</span>
                </div>

            </div>

            <div class="input-container">
                <input type="submit" class="submit-btn" value="Criar meu Burger!">
            </div>


        </form>

    </div>

  </div>

</template>

<script>
import { nullLiteral } from '@babel/types'
import { effect } from '@vue/reactivity'


    export default {
        name: 'BurgerForm',
        data() {
            return {
                paes: null,
                carmes: null,
                opcionaisdata: null,
                
                nome: null,
                pao: null,
                carne: null,
                opcionais: [],
                status: "Solicitado",
                msg: null
            }
        },
        methods:{
            async getIngredientes(){
                const req = await fetch("http://localhost:3000/ingredientes");
                const data = await req.json();

                this.paes = data.paes;
                this.carnes = data.carnes;
                this.opcionaisdata = data.opcionais;
            }

        },
        mounted(){
            this.getIngredientes()
        }
    }

</script>

<style scoped>
    #burger-form{
        width: 300px;
        margin: auto;
    }

    .input-container{
        display: flex;
        flex-direction: column;
        margin-bottom: 20px;
    }

    label{
        font-weight: bold;
        margin-bottom: 15px;
        color: #222;
        padding: 5px 10px;
        border-left: 4px solid #fcba03;
    }

    input, select{
        padding: 5px 10px;
        background: none;
        border-radius: 6px;
        width: 300px;
    }

    #opcionais-container{
        flex-direction: row;
        flex-wrap: wrap;
    }

    #opcionais-title{
        width: 100%;
    }
    
    .checkbox-container{
        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-bottom: 20px;
    }

    .checkbox-container span, 
    .checkbox-container input{
        width: auto;
        padding-left: 10px;
        font-weight: bold;
    }
    
    

    .submit-btn{
        background-color: #222;
        color: #fcba03;
        font-weight: bold;
        padding: 10px;
        border: 2px solid #222;
        font-size: 16px;
        margin: 0 auto;
        cursor: pointer;
        transition: .5s;
    }

    .submit-btn:hover{
        background-color: transparent;
        color: #222;
        
    }

</style>