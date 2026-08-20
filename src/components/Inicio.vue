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
        :etapa="etapa"
        :letras="letras"
        /> 

    </section>
   
    <section v-if="tela === 'jogo'" id="inicio">
       <Jogo
       :erros="erros"
       :palavra="palavra"
       :dica="dica"
       :verificarLetra="verificarLetra"
       :jogar="jogar"
       :etapa="etapa"
       :letras="letras"
       :jogarNovamente="jogarNovamente"
       />

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
            dica: '',
            erros: 0,
            letras: []
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
        },
        verificarLetra: function (letra) {
            return this.letras.find(item => item.toLowerCase() === letra.toLowerCase());
        },
        jogar: function (letra) {
            /* Adiciona letra jogada */
            this.letras.push(letra);

            /* validar erro */
            this.verificarErros(letra);
        },
        verificarErros: function(letra){
            /* acerto */
            if (this.palavra.toLowerCase().indexOf(letra.toLowerCase()) >= 0) {
                return this.verificarAcertos();
            }

            /* erros */
            this.erros++;

            /* enforcado */
            if (this.erros === 6) {
                this.etapa = 'enforcado'
            }
        },
        verificarAcertos: function () {
            let letrasUnicas = [...new Set(this.palavra.split(''))] /* criar array com letras separadas da palavra */
            if (letrasUnicas.length === (this.letras.length - this.erros)) {
                this.etapa = 'ganhador';
            }
        },
        jogarNovamente: function () {
            this.palavra = '';
            this.dica = '';
            this.erros = 0;
            this.letras = [];
            this.tela = 'inicio';
            this.etapa = 'palavra';
        }
    }
}
</script>

<style>
h1{
    color: red;
}
</style>
