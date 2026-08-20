<template>
   <div class="teclado">
      <button 
      type="button" 
      class="teclado-botao"
      v-for="(letra, key) in alfabeto"
      :key="key"
      :disabled="verificarLetra(letra)"
      @click="jogar(letra)"
      >
        {{ letra }}
      </button>
   </div>
</template>

<script>

export default {
    name: 'palavra',
    props: {
        letras: Array,
        verificarLetra: Function,
        jogar: Function
    },
    data() {
        return {
                alfabeto: "abcdefghijklmnopqrstuvwxyz".split("")
        }
    }
}
</script>

<style>
.teclado{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    width: 80%;
    margin-top: 20px;
}

.teclado-botao{
    margin: 5px;
    text-transform: uppercase;
}
</style>