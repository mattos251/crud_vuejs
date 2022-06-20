<template>
  <div id="main-form">
    <p> Componente de mensagem </p>

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
                    <option value="Caseiro">Caseiro</option>
                    <option value="integral">Integral</option>
                    
                </select>

            </div>

            <div class="input-container">
                <label for="carne"> Escolha a carne do seu burger: </label>

                <select name="carne" id="carne" v-model="carne">
                    <option value="">Selecione o tipo de carne</option>
                    <option value="maminha">Maminha</option>
                    <option value="alcatra">Alcatra</option>
                    <option value="picanha">Picanha</option>
                    <option value="alcatra">Veggie burger</option>
                </select>

            </div>

            <div class="input-container">
                <label for="opcionais"> Selecione outras opções: </label>

                <div class="checkbox-container" >
                    <input type="checkbox" name="opcionais" v-model="opcionais" value="opcionais">
                    <span> Salame</span>

                    <input type="checkbox" name="opcionais" v-model="opcionais" value="opcionais">
                    <span> Bacon</span>

                    <input type="checkbox" name="opcionais" v-model="opcionais" value="opcionais">
                    <span> Cheddar</span>

                    <input type="checkbox" name="opcionais" v-model="opcionais" value="opcionais">
                    <span> Cebola roxa</span>
  
                </div>

            </div>
        </form>

    </div>

  </div>

</template>

<script>

    export default {
        nome: 'BurgerForm'
    }

</script>

<style>

</style>