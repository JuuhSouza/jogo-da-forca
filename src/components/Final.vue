<template>
   <div class="final">
    <button 
        type="button"
        @click="jogarNovamente"
        class="final-botao">
            Jogar novamente
        </button>

     <div :class="`final-texto ${etapa}`">
        <h3>{{texto}}</h3>
     </div>
   </div>
</template>

<script>

export default {
    name: 'final',
    props: {
        etapa: String,
        texto: String,
        jogarNovamente: Function
    }
}
</script>

<style>
.final-texto{
    margin: 20px 0px;
    font-size: 24px;
    font-weight: bold;
    color: white;
}

.final-texto.enforcado{
    color: red;
}

.final-texto.ganhador{
    color: green;
}

.final-botao {
    margin: 2rem;
    font-size: 1.2rem;
}
</style>