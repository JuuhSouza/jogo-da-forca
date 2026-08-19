<template>
    <h1> Jogo da forca</h1>

    <section v-if="tela === 'inicio'" id="inicio">
        <formulario 
        v-if="etapa === 'palavra'"
        title="Defina a palavra"
        button="Próximo"
        :action="setPalavra"
        />
        
        <formulario 
        v-if="etapa === 'dica'"
        title="Defina a dica"
        button="Iniciar jogo"
        :action="setDica"
        />

    </section>
   
    <section v-if="tela === 'jogo'" id="inicio">
       <Jogo/>

    </section>

</template>

<script>
import formulario from './Formulario.vue';
import Jogo from './Jogo.vue';

export default {
    data() {
        return {
            tela: 'inicio',
            etapa: 'palavra',
            palavra: '',
            dica: ''
        }
    },
    components: {
        formulario, Jogo
    },
    methods: {
        setPalavra: function (palavra) {
            this.palavra = palavra;
            this.etapa = 'dica';
        },
        setDica: function (dica) {
            this.dica = dica;
            this.etapa = 'jogo';
            this.tela = 'jogo';
        }
    }
}
</script>

<style>
h1{
    color: red;
}
</style>
